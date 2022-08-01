# PendingOperation

A reference to an ongoing asynchronous SDK operation, whose result is not yet known. It provides methods for checking whether the operation is complete, and whether it has succeeded. Additionally, it offers the ability to get its result either synchronously (blocking), or asynchronously via listeners.

If the operation succeeds, all completion and success listeners will be notified. The result will also be made available via the [`getResult()`](./#getresult) method. If the operation fails, all completion and failure listeners will be notified, and the error will be made available via the [`getError()`](./#geterror) method.

## PendingOperation API

### `addOnCompleteListener`

> ```java
> PendingOperation<Result,Error> addOnCompleteListener(OnCompleteListener<Result, Error> listener)
> ```
>
> Adds an [OnCompleteListener](oncompletelistener.md) that will be invoked after the operation completes.

### `addOnSuccessListener`

> ```java
> PendingOperation<Result,Error> addOnSuccessListener(OnSuccessListener<Result> listener)
> ```
>
> Adds an [OnSuccessListener](onsuccesslistener.md) that will be invoked after the operation succeeds.

### `addOnFailureListener`

> ```java
> PendingOperation<Result,Error> addOnFailureListener(OnFailureListener<Error> listener)
> ```
>
> Adds an [OnFailureListener](onfailurelistener-1.md) that will be invoked after the operation fails.

### `isComplete`

> ```java
> boolean isComplete()
> ```
>
> Returns whether the operation has completed. If `true`, you can call `isSuccessful()` to check whether it succeeded.

### `isSuccessful`

> ```java
> boolean isSuccessful()
> ```
>
> Returns whether the operation has succeeded. If this method returns `true`, you can call `getResult()` to obtain the result. Otherwise if it returns `false`, you can call `getError()` to obtain the error.

### `waitFor`

> ```java
> PendingOperation<Result, Error> waitFor(int timeout, TimeUnit unit)
> ```
>
> Waits till the operation is complete for the duration that is specified. Call {@link #isComplete()} after this method, to check whether the operation completed or if this method timed out.
>
> @throws `InterruptedException` if thread is interrupted while waiting

### `waitTillCompletion`

> ```java
> PendingOperation<Result, Error> waitTillCompletion()
> ```
>
> Waits till the operation is complete.
>
> throws `InterruptedException` if thread is interrupted while waiting.

### `getResult`

> ```java
> Result getResult()
> ```
>
> Returns the result of the operation.
>
> throws `InterruptedException` if thread is interrupted while waiting. throws `SdkException` if the operation has failed.

### `getResultOrNull`

> ```java
> Result getResultOrNull()
> ```
>
> Returns the result of the operation if it completed successfully. Otherwise returns `null`.

### `getError`

> ```java
> Error getError()
> ```
>
> Returns the error encountered during the operation.
>
> throws `IllegalStateException` if the operation is not yet complete. throws `SdkException` if the PendingOperation has succeeded.
