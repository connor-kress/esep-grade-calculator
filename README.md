# ESEP Grade Calculator

Go library that calculates a student's final letter grade (or pass/fail result) from weighted averages of their assignment, exam, and essay grades.

## Files

```
.
|-- README.md
|-- grade-calculator/
    |-- go.mod                    # Go module (`module esep/grade-calculator`)
    |-- grade_calculator.go       # Library code (package esepunittests)
    |-- grade_calculator_test.go  # Unit tests
```

No external dependencies.

## Requirements

- [Go](https://go.dev/doc/install) 1.24.4+ (see `grade-calculator/go.mod`)

## Example

```go
gradeCalculator := NewGradeCalculator(false)
gradeCalculator.AddGrade("example assignment", 100, Assignment)
gradeCalculator.AddGrade("example exam", 80, Exam)
gradeCalculator.AddGrade("example essay", 90, Essay)
letterGrade := gradeCalculator.GetFinalGrade()
```

- `NewGradeCalculator(passFail)`: creates an empty calculator; `true` for pass/fail, `false` for letter grades.
- `AddGrade(name, grade, gradeType)`: records a grade of type `Assignment`, `Exam`, or `Essay`.
- `GetFinalGrade()`: returns `"A"`, `"B"`, `"C"`, `"D"`, or `"F"`; in pass/fail mode, `"Pass"` (C or better) or `"Fail"`.

## Tests

Run from `grade-calculator/` (hyphen, not underscore):

```bash
cd grade-calculator/
go test ./...  # all tests
go test -v ./...  # verbose
go test -run TestGetGradeA ./...  # single test
```

## Coverage

```bash
go test -cover ./...  # coverage percentage
go test -coverprofile=coverage.txt ./...  # write coverage profile
go tool cover -func=coverage.txt  # per-function coverage
go tool cover -html=coverage.txt  # line-by-line HTML report
```

## Links

- [Go testing package](https://pkg.go.dev/testing)
- [Go `cover` tool](https://pkg.go.dev/cmd/cover)
- [Go blog cover story](https://go.dev/blog/cover)
