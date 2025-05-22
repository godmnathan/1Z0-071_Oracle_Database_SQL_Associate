# Contributing to Oracle Database SQL Associate (1Z0-071) Guide

Thank you for your interest in contributing to this Oracle SQL certification guide! This document provides guidelines and instructions for contributing to make the process smooth and effective.

## 🌟 Ways to Contribute

There are many ways you can contribute to this project:

1. **Content Improvements**
   - Add detailed explanations for complex topics
   - Create new examples that demonstrate SQL concepts
   - Develop practice exercises with solutions
   - Design visual aids like diagrams or flowcharts

2. **Technical Contributions**
   - Fix bugs in SQL scripts or example code
   - Improve database setup scripts
   - Enhance the repository structure
   - Add automation tools or utilities

3. **Documentation**
   - Fix typos or grammatical errors
   - Improve clarity of explanations
   - Update content to reflect latest Oracle versions
   - Translate content to other languages

4. **Community Support**
   - Answer questions in discussions
   - Review and provide feedback on pull requests
   - Help maintain the issue tracker
   - Share your experience with the certification exam

## 📝 Contribution Process

### 1. Find or Create an Issue

- Check the [Issues](https://github.com/godmnathan/1Z0-071_Oracle_Database_SQL_Associate/issues) page to see if your contribution idea already exists
- If not, create a new issue describing what you'd like to contribute
- Wait for feedback or approval before starting work on major changes

### 2. Fork and Clone the Repository

```bash
# Fork the repository on GitHub, then:
git clone https://github.com/YOUR-USERNAME/1Z0-071_Oracle_Database_SQL_Associate.git
cd 1Z0-071_Oracle_Database_SQL_Associate
git remote add upstream https://github.com/godmnathan/1Z0-071_Oracle_Database_SQL_Associate.git
```

### 3. Create a Branch

```bash
git checkout -b feature/your-feature-name
```

Use a descriptive branch name that reflects your contribution.

### 4. Make Your Changes

- Follow the style and formatting of existing content
- Add comments to SQL code to explain complex operations
- Test all code examples to ensure they work correctly
- Update relevant documentation if needed

### 5. Commit Your Changes

```bash
git add .
git commit -m "Add detailed explanation of subqueries with examples"
```

Write clear, concise commit messages that explain your changes.

### 6. Stay Updated

```bash
git fetch upstream
git rebase upstream/main
```

### 7. Push Your Changes

```bash
git push origin feature/your-feature-name
```

### 8. Create a Pull Request

- Go to the [repository](https://github.com/godmnathan/1Z0-071_Oracle_Database_SQL_Associate) on GitHub
- Click "Pull Request"
- Select your branch and provide a clear description of your changes
- Link to any related issues

## 📋 Content Guidelines

### SQL Examples

- Include comments explaining the purpose and functionality
- Use consistent formatting and indentation
- Provide sample output where appropriate
- Use the sample database tables for consistency

Example:
```sql
-- Find employees with salaries higher than their department average
SELECT e.employee_id, e.first_name, e.last_name, e.salary, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id
WHERE e.salary > (
    SELECT AVG(salary)
    FROM employees
    WHERE department_id = e.department_id
)
ORDER BY d.department_name, e.salary DESC;
```

### Documentation

- Use clear, concise language
- Break down complex concepts into digestible parts
- Include relevant links to official Oracle documentation
- Use markdown formatting for readability

### Diagrams and Visual Aids

- Use SVG format when possible for better scaling
- Include source files for diagrams (e.g., draw.io XML)
- Provide alt text for accessibility
- Keep file sizes reasonable

## 🧪 Testing Guidelines

- Test all SQL examples against Oracle Database 19c or later
- Verify that examples work with the provided sample database
- Check for edge cases and NULL handling
- Ensure examples demonstrate best practices

## 📚 Style Guide

- Use consistent naming conventions
  - Table names: singular nouns (e.g., `employee` not `employees`)
  - Column names: lowercase with underscores (e.g., `first_name`)
  - SQL keywords: UPPERCASE (e.g., `SELECT`, `FROM`, `WHERE`)
- Format SQL for readability:
  - One clause per line for complex queries
  - Consistent indentation (2 or 4 spaces)
  - Align related items vertically when appropriate

## 🔄 Review Process

All contributions will go through a review process:

1. Automated checks for formatting and basic errors
2. Peer review by at least one maintainer
3. Feedback and requested changes if necessary
4. Approval and merge when ready

## 📜 License

By contributing, you agree that your contributions will be licensed under the project's [Unlicense](LICENSE) license.

## 🙏 Recognition

All contributors will be acknowledged in the repository's README and/or a dedicated CONTRIBUTORS file.

---

Thank you for helping make this Oracle SQL certification guide better for everyone! Your contributions are greatly appreciated.
