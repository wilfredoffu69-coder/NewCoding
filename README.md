# gpacalc

A small, dependency-free Python library for calculating a student's
**semester GPA** and **cumulative CGPA** from a list of courses (name,
credit hours, letter grade). Ships with a default grading scale used
at many Ghanaian tertiary institutions, but you can supply your own.

## Install

```bash
pip install .
```

Or just drop the `gpacalc/` folder into your project — no external
dependencies required.

## Quick start

```python
from gpacalc import GPACalculator, Course

# --- Single semester GPA ---
calc = GPACalculator()
calc.add_course("MATH 101", 3, "A")
calc.add_course("ENG 101", 2, "B+")
print(calc.gpa())                 # 3.8
print(calc.total_credit_hours())  # 5

# --- Cumulative GPA (CGPA) across multiple semesters ---
sem1 = [Course("MATH 101", 3, "A"), Course("ENG 101", 2, "B")]
sem2 = [Course("PHY 201", 3, "C+")]
print(calc.cgpa([sem1, sem2]))    # 3.1875

# --- Degree classification ---
print(GPACalculator.classify(3.8))  # "First Class"
```

## Custom grading scale

```python
from gpacalc import GradeScale, GPACalculator

my_scale = GradeScale({"A": 4.0, "B": 3.0, "C": 2.0, "D": 1.0, "F": 0.0})
calc = GPACalculator(scale=my_scale)
```

## Running tests

```bash
pip install pytest
pytest tests/
```

Every public function also has runnable doctest examples in its
docstring.

## License

MIT
