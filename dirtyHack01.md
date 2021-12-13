# DirtyHack01

```java
/**
 * @param message to send to the server.
 * @throws IOException if a connection error occurs.
 */
void sendSynchronous(Message message) throws IOException {
    Objects.requireNonNull(message);
    try {
        Callable<Optional<IOException>> callable = () -> {
            try {
                client.send(message);
                return Optional.empty();
            } catch (IOException e) {
                return Optional.of(e);
            }
        };
        Optional<IOException> exception = executorService.submit(callable).get();
        if (exception.isPresent()) throw exception.get();
    } catch (ExecutionException | InterruptedException e) {
        throw new IOException(e);
    }
}
```
