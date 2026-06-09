# 63. Date & Time

On the JVM, Kotlin uses the `java.time` package. Its types are immutable, so methods like `plusDays` return a new value rather than mutating in place. We use fixed dates here so the output is deterministic — in real code you would reach for `LocalDate.now()`.

```kotlin
import java.time.LocalDate
import java.time.LocalDateTime
import java.time.Duration
import java.time.Period
import java.time.format.DateTimeFormatter

fun main() {
    val date = LocalDate.of(2024, 1, 15)
    println(date)
    println(date.plusDays(20))           // immutable: returns a new date

    val launch = LocalDateTime.of(2024, 1, 15, 9, 30)
    val formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm")
    println(launch.format(formatter))
}
```

`Period` measures a span in years/months/days between two dates, while `Duration` measures a time-based amount in hours/minutes/seconds.

```kotlin
val period = Period.between(LocalDate.of(2024, 1, 1), LocalDate.of(2024, 3, 15))
println("${period.months} months, ${period.days} days")

val duration = Duration.ofHours(2).plusMinutes(30)
println("${duration.toMinutes()} minutes")
```

Kotlin also has its own multiplatform `kotlin.time.Duration`, created with extensions like `2.hours` and `30.minutes`; it is independent of `java.time` and works on every target.

Running it:

```
$ kotlin run
2024-01-15
2024-02-04
2024-01-15 09:30
2 months, 14 days
150 minutes
```

[← Prev](62-sorting.md) | [Index](../README.md) | [Next →](64-random.md)
