# 67. Testing

The `kotlin.test` library gives you a small, multiplatform set of assertions that delegate to a real test framework (JUnit on the JVM) at run time. It needs the `kotlin-test` dependency. Tests are run with the toolchain's `kotlin test` command, not with `kotlin run`.

```kotlin
import kotlin.test.Test
import kotlin.test.assertEquals
import kotlin.test.assertTrue
import kotlin.test.assertFailsWith

fun add(a: Int, b: Int): Int = a + b

fun divide(a: Int, b: Int): Int =
    if (b == 0) throw IllegalArgumentException("divide by zero") else a / b

class CalculatorTest {
    @Test
    fun addsNumbers() {
        assertEquals(5, add(2, 3))
    }

    @Test
    fun resultIsPositive() {
        assertTrue(add(2, 3) > 0)
    }

    @Test
    fun rejectsZeroDivisor() {
        assertFailsWith<IllegalArgumentException> {
            divide(1, 0)
        }
    }
}
```

Each `@Test` function is one isolated check. `assertEquals(expected, actual)` compares values, `assertTrue` checks a boolean, and `assertFailsWith<T> { }` asserts that the block throws the given exception type — returning the exception so you can inspect its message if needed.

Tests live under a `test/` directory (alongside `src/`). Set `product: jvm/lib` and add the `$kotlin.test` dependency in `module.yaml`, then run the suite with `kotlin test`:

```yaml
product: jvm/lib

dependencies:
  - $kotlin.test
```

Running it:

```
$ kotlin test
Started CalculatorTest
Started addsNumbers()
Passed addsNumbers()
Started resultIsPositive()
Passed resultIsPositive()
Started rejectsZeroDivisor()
Passed rejectsZeroDivisor()
Completed CalculatorTest

Test run finished after 85 ms
[         3 tests found           ]
[         3 tests started         ]
[         0 tests failed          ]
[         3 tests successful      ]
```

[← Prev](66-dsl.md) | [Index](../README.md)
