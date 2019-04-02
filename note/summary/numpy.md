# numpy

## code structure

- [include/numpy](https://github.com/numpy/numpy/tree/master/numpy/core/include/numpy)
- [src](https://github.com/numpy/numpy/tree/master/numpy/core/src)

## `np.ndarray`

### internal

### `np.array`

- [_array_fromobject](https://github.com/numpy/numpy/blob/master/numpy/core/src/multiarray/multiarraymodule.c#L1575)
- [PyArray_CheckFromAny](https://github.com/numpy/numpy/blob/master/numpy/core/src/multiarray/ctors.c#L1974)
- [PyArray_FromAny](https://github.com/numpy/numpy/blob/master/numpy/core/src/multiarray/ctors.c#L1793)
- [PyArray_NewFromDescr](https://github.com/numpy/numpy/blob/master/numpy/core/src/multiarray/ctors.c#L1162)
- [PyArray_NewFromDescrAndBase](https://github.com/numpy/numpy/blob/master/numpy/core/src/multiarray/ctors.c#L1176)
- [PyArray_NewFromDescr_int](https://github.com/numpy/numpy/blob/master/numpy/core/src/multiarray/ctors.c#L909)

### `_array_fill_strides`

- [_array_fill_strides](https://github.com/numpy/numpy/blob/master/numpy/core/src/multiarray/ctors.c#L4011)

```c
NPY_NO_EXPORT void
_array_fill_strides(npy_intp *strides, npy_intp *dims, int nd, size_t itemsize,
                    int inflag, int *objflags)
{
    int i;

    /* Only make Fortran strides if not contiguous as well */
    if ((inflag & (NPY_ARRAY_F_CONTIGUOUS|NPY_ARRAY_C_CONTIGUOUS)) ==
                                            NPY_ARRAY_F_CONTIGUOUS) {
        // omit
    }
    else {
        for (i = nd - 1; i >= 0; i--) {
            strides[i] = itemsize;
            if (dims[i]) {
                itemsize *= dims[i];
            }
        }
    }
    return;
}
```
