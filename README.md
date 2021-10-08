# vlibtcc
V wrapper for libtcc

Example usage 

```
import vlibtcc
type Func = fn() int
s:=vlibtcc.tcc_new()
vlibtcc.tcc_set_output_type(s,1)
program:='#include <stdio.h>
			int entry(){
				printf("Hello World!");
				return 0;
			}'
vlibtcc.tcc_compile_string(s,&char(program.str))
vlibtcc.tcc_relocate(s, voidptr(1))
entry := Func(vlibtcc.tcc_get_symbol(s, &char("entry".str)))
entry()
vlibtcc.tcc_delete(s)
```
