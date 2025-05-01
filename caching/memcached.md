# Memcache

Memcache is a free open source, high-performance, distributed memory object caching system.

In contrast with Redis (which is another key-value data store), it is simpler.

```js
// The constructor of a new cache includes the server location and options.
var memcached = new Memcached(Server locations, options);
```

### Functions

- get - get a value from the cache based on a key
- set - add a new value into the cache with a new ket

### Sources

- [docs](https://memcached.org/)
- [npm and memcache](https://www.npmjs.com/package/memcached)
