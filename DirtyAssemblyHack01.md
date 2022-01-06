# Your typical multiplication  

```assembly
mul_u32         PROC
                EXPORT mul_u32
                IMPORT display_title
                IMPORT tests_32x32
                PUSH {R1-R3,LR}

	  	LDR  R0,=title
		BL   display_title

		LDR  R3,=result_table
		LDR  R2,=values
		LDR  R1,=NR_OF_TESTS
		LDR  R0,=operation
		BL   tests_32x32

		POP  {R1-R3,PC}
		ENDP
```		
