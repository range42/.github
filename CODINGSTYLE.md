# Coding Guidelines for Range42 Developers

Maintaining proper coding style is very important for any large software project, such as Range42. Here's why:

- It eases maintenance tasks, such as adding new functionality or generalizing code later
- It allows others (as well as the future you!) to easily understand fragments of code and what they were supposed to do, and thus makes it easier to later extend them with newer functionality or bug fixes
- It allows others to easily review the code and catch bugs
- It provides for an aesthetically pleasing experience when one reads the code

## General Typographic Conventions

- Maintain a maximum line length of 120 characters for modern development environments. This allows for better readability on today's displays while still enabling side-by-side code windows.
- Naming conventions:
    - `ClassName` (PascalCase)
    - `someVariable`, `someFunction`, `someArgument` (camelCase)
    - `CONSTANT_VALUE` (SCREAMING_SNAKE_CASE)
    - `package-name`, `file-name` (kebab-case for files and packages)
- Maintain decent horizontal spacing, e.g. add a space after `if` or before `{` in JavaScript, TypeScript, Python, and similar in other languages. Whether and where to also use spaces within expressions, such as `(y*4+8)` vs. `(y * 4 + 8)` is left to the developer's judgment. Do not put spaces immediately after or before the brackets in expressions, so avoid constructs like this: `if ( condition )` and use ones like this: `if (condition)` instead.
- Use descriptive names for variables and functions. At a time when most editors have auto-completion features, there is no excuse for using short variable names.
- Comments should be indented together with the code, e.g. like this:
    ```typescript
    class ScenarioEngine {
        /** @var AssessmentConfig */
        private assessmentConfig: AssessmentConfig;
    }
    ```

## File Naming Conventions

- Never use spaces within file names
- **TypeScript/JavaScript:** Write file names with small letters, use dashes to separate words, e.g. `scenario-engine.ts`, `assessment-validator.js`
- **Python:** Write file names with small letters, use underscores to separate words, e.g. `load_scenarios.py`, `validate_infrastructure.py`
- **Go:** Write file names with small letters, use underscores for multiple words, e.g. `scenario_runner.go`, `assessment_engine.go`
- **YAML/JSON:** Use kebab-case for configuration files, e.g. `network-config.yaml`, `scenario-definition.json`
- **Docker:** Use descriptive names with tags, e.g. `Dockerfile.scenario-runner`, `docker-compose.dev.yml`

## Language-Specific Guidelines

### TypeScript/JavaScript
```typescript
// Good
class ScenarioRunner {
    private readonly scenarios: Scenario[];
    
    public async executeScenario(scenarioId: string): Promise<ExecutionResult> {
        const scenario = this.findScenario(scenarioId);
        if (!scenario) {
            throw new Error(`Scenario not found: ${scenarioId}`);
        }
        return await this.runScenario(scenario);
    }
}

// Avoid
class sr {
    private s: any[];
    public exec(id: string) {
        // unclear implementation
    }
}
```

### Python
```python
# Good
class AssessmentEngine:
    def __init__(self, config: AssessmentConfig) -> None:
        self.config = config
        self.evaluators: List[Evaluator] = []

    def evaluate_submission(self, submission: Submission) -> Score:
        """Evaluate a student's submission against scenario criteria."""
        total_score = 0
        for evaluator in self.evaluators:
            total_score += evaluator.calculate_score(submission)
        return Score(total_score)

# Avoid
class ae:
    def __init__(self, c):
        self.c = c
        self.e = []
```

### Go
```go
// Good
type ScenarioConfig struct {
    Name        string            `json:"name"`
    Description string            `json:"description"`
    Resources   map[string]string `json:"resources"`
}

func (s *ScenarioRunner) DeployScenario(ctx context.Context, config ScenarioConfig) error {
    if err := s.validateConfig(config); err != nil {
        return fmt.Errorf("invalid scenario config: %w", err)
    }
    return s.deploy(ctx, config)
}

// Avoid
type SC struct {
    N string
    D string
    R map[string]string
}
```

## General Programming Style Guidelines

- Always prefer readability over cleverness! No need to use tricks to save a few lines of code.
- Make sure your code compiles and builds without warnings
- Always think first about interfaces (e.g. function arguments, or class methods) and data structures before you start writing the actual code.
- Use comments to explain non-trivial code fragments, or expected behavior of more complex functions, if it is not clear from their name.
- Do not use comments for code fragments where it is immediately clear what the code does. E.g. avoid constructs like this:

    ```javascript
    function returnStyle(type, style, content) {
        currentType = type; 
        currentContent = content;
        // Return style
        return style;
    }
    ```

- In production code, there should be little to no commented or disabled code fragments. Do not use comments to disable code fragments, unless you need to. But generally, there is little excuse to keep old, unused code fragments in the code. Instead, use the functionality provided by the source code management system, such as git. For example, create a special branch for storing the old, unused code – this way you will always be able to merge this code into upstream in the future.
- Try not to hardcode values in the code. Use configuration files, environment variables, or constants.

## Security Guidelines

Given Range42's cybersecurity focus, special attention must be paid to secure coding practices:

- **Input Validation:** Always validate and sanitize all inputs, especially in scenario configurations and user-provided data
- **Secrets Management:** Never hardcode credentials, API keys, or sensitive data. Use environment variables or secure secret management systems
- **Error Handling:** Don't expose sensitive information in error messages. Log detailed errors server-side but return generic messages to clients
- **Dependencies:** Regularly update dependencies and scan for known vulnerabilities
- **Logging:** Log security-relevant events but avoid logging sensitive data

```typescript
// Good
class UserAuth {
    async authenticateUser(credentials: UserCredentials): Promise<AuthResult> {
        try {
            const user = await this.validateCredentials(credentials);
            this.logger.info('User authentication successful', { userId: user.id });
            return { success: true, user };
        } catch (error) {
            this.logger.error('Authentication failed', { error: error.message });
            return { success: false, message: 'Invalid credentials' };
        }
    }
}

// Avoid
class UserAuth {
    async auth(creds: any) {
        const user = await db.query(`SELECT * FROM users WHERE email='${creds.email}' AND password='${creds.password}'`);
        return user;
    }
}
```

## Configuration and Infrastructure

- **Infrastructure as Code:** Use descriptive names and proper indentation in YAML/JSON files
- **Environment Separation:** Clearly separate development, staging, and production configurations
- **Documentation:** Include comments in configuration files explaining non-obvious settings

```yaml
# Good
apiVersion: v1
kind: ConfigMap
metadata:
  name: scenario-config
  namespace: range42-scenarios
data:
  # Maximum number of concurrent scenario instances
  max_concurrent_scenarios: "10"
  # Timeout for scenario cleanup in minutes
  cleanup_timeout_minutes: "30"
  # Network isolation policy for training environments
  network_isolation_policy: "strict"
```

## Testing Guidelines

- Write tests for all new functionality
- Use descriptive test names that explain what is being tested
- Follow the Arrange-Act-Assert pattern
- Include both positive and negative test cases

```typescript
describe('ScenarioRunner', () => {
    it('should successfully deploy a valid scenario configuration', async () => {
        // Arrange
        const validConfig = createValidScenarioConfig();
        const runner = new ScenarioRunner();

        // Act
        const result = await runner.deployScenario(validConfig);

        // Assert
        expect(result.success).toBe(true);
        expect(result.deploymentId).toBeDefined();
    });

    it('should reject scenario configuration with missing required fields', async () => {
        // Arrange
        const invalidConfig = createConfigMissingRequiredFields();
        const runner = new ScenarioRunner();

        // Act & Assert
        await expect(runner.deployScenario(invalidConfig))
            .rejects
            .toThrow('Missing required configuration fields');
    });
});
```

## Commit Message Guidelines

Please follow our [commit message best practices](https://github.com/Range42/core/wiki/CommitMessageBestPractices) when writing your git commit messages.

Use conventional commits format:
```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

Types:
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `style:` - Code style changes (formatting, missing semicolons, etc.)
- `refactor:` - Code refactoring
- `test:` - Adding or updating tests
- `chore:` - Maintenance tasks

Examples:
```
feat(scenarios): add network penetration testing scenario
fix(assessment): resolve scoring calculation for time-based challenges
docs(api): update authentication endpoint documentation
test(infrastructure): add deployment validation tests
```

When committing changes that resolve an issue, include `#NNNN` in the commit message, where NNNN is the issue number:
```
fix(scenarios): resolve container startup race condition (#1234)
```

## Code Review Guidelines

- **Be constructive:** Provide specific, actionable feedback
- **Security focus:** Pay special attention to security implications
- **Performance:** Consider the performance impact of changes
- **Documentation:** Ensure new features are properly documented
- **Testing:** Verify that appropriate tests are included

Remember: Good code is not just functional – it's readable, maintainable, secure, and well-tested.
