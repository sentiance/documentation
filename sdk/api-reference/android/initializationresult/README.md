# InitializationResult

## InitializationResult API

### `isSuccessful()`

> ```java
> boolean isSuccessful()
> ```

### `getFailureReason()`

> ```java
> @Nullable InitializationFailureReason getFailureReason()
> ```
>
> Returns the [`InitializationFailureReason`](initializationfailurereason.md), returns `null` if initialization was successful.

### `getThrowable()`

> ```java
> @Nullable Throwable getThrowable()
> ```
>
> Returns the exception thrown during initialization.
