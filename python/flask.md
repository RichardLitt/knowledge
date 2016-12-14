## Random notes on Flask

_When you are enlightened, write it down._

- UserMixin doesn't have a query function; this is because the `load_user()` function was not returning a user, rather an instance of the user class with only the `id` populated.