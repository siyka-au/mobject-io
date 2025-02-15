# Converters

## Problem
Conversion between types can be handled in TwinCAT using the standard __TYPE\_TO\_TYPE__ operators.  The problem with this is that they do not indicate if a conversion is possible.  For example you can convert a LREAL to a BYTE if the value is between 0 and 255 with no decimal place. If the value is outside of this range then 0 is returned, and the operation fails silently.

## Solution
mobject-core is equipped with basic type converters, which both convert and validate the conversion by returning a [HRESULT](https://infosys.beckhoff.com/english.php?content=../content/1033/tf7xxx_tc3_vision/2334733579.html).  The conversion only takes place if possible, otherwise the initial value is retained. 

## Examples

When the destination type is known you can use the function __Convert\_TYPE\_TO\_TYPE__

```declaration
PROGRAM Main
VAR
   number : LREAL;
   destination : BYTE;
   result : HRESULT;
END_VAR
```
```body
   number := 123.0;
   result := Convert_LREAL_TO_BYTE(number,destination);  // destination = 123, result = S_OK
   number := 123.5;
   result := Convert_LREAL_TO_BYTE(number,destination);  // destination = no change, result = INCOMPATIBLE
```

When the destination type is unknown, i.e. when used with a function which supports ANY you can use the function __Convert\_TYPE\_TO\___ and the type will be discovered automatically.

```declaration
PROGRAM Main
VAR
   number : LREAL;
   destination1 : BYTE;
   destination2 : INT;
   destination3 : REAL;
   destination4 : STRING;
   result : HRESULT;
END_VAR
```
```body
   number := 123.0;
   result := Convert_LREAL_TO_(number,destination1);  // destination1 = 123, result = S_OK
   result := Convert_LREAL_TO_(number,destination2);  // destination2 = 123, result = S_OK
   result := Convert_LREAL_TO_(number,destination3);  // destination3 = 123.0, result = S_OK
   result := Convert_LREAL_TO_(number,destination4);  // destination4 = '123.0', result = S_OK
```

## Supported Conversions 
### Untyped 
* Convert_BOOL_TO_(in, out)
* Convert_BYTE_TO_(in, out)
* Convert_DATE_TO_(in, out)
* Convert_DINT_TO_(in, out)
* Convert_DT_TO_(in, out)
* Convert_DWORD_TO_(in, out)
* Convert_INT_TO_(in, out)
* Convert_LINT_TO_(in, out)
* Convert_LREAL_TO_(in, out)
* Convert_LWORD_TO_(in, out)
* Convert_REAL_TO_(in, out)
* Convert_SINT_TO_(in, out)
* Convert_STRING_TO_(in, out)
* Convert_TIME_TO_(in, out)
* Convert_TOD_TO_(in, out)
* Convert_UDINT_TO_(in, out)
* Convert_UINT_TO_(in, out)
* Convert_ULINT_TO_(in, out)
* Convert_USINT_TO_(in, out)
* Convert_WORD_TO_(in, out)

### Typed
* Convert_BOOL_TO_BOOL(in, out)
* Convert_BOOL_TO_BYTE(in, out)
* Convert_BOOL_TO_DATE(in, out)
* Convert_BOOL_TO_DINT(in, out)
* Convert_BOOL_TO_DT(in, out)
* Convert_BOOL_TO_DWORD(in, out)
* Convert_BOOL_TO_INT(in, out)
* Convert_BOOL_TO_LINT(in, out)
* Convert_BOOL_TO_LREAL(in, out)
* Convert_BOOL_TO_LWORD(in, out)
* Convert_BOOL_TO_REAL(in, out)
* Convert_BOOL_TO_SINT(in, out)
* Convert_BOOL_TO_STRING(in, out)
* Convert_BOOL_TO_TIME(in, out)
* Convert_BOOL_TO_TOD(in, out)
* Convert_BOOL_TO_UDINT(in, out)
* Convert_BOOL_TO_UINT(in, out)
* Convert_BOOL_TO_ULINT(in, out)
* Convert_BOOL_TO_USINT(in, out)
* Convert_BOOL_TO_WORD(in, out)
* Convert_BYTE_TO_BOOL(in, out)
* Convert_BYTE_TO_BYTE(in, out)
* Convert_BYTE_TO_DATE(in, out)
* Convert_BYTE_TO_DINT(in, out)
* Convert_BYTE_TO_DT(in, out)
* Convert_BYTE_TO_DWORD(in, out)
* Convert_BYTE_TO_INT(in, out)
* Convert_BYTE_TO_LINT(in, out)
* Convert_BYTE_TO_LREAL(in, out)
* Convert_BYTE_TO_LWORD(in, out)
* Convert_BYTE_TO_REAL(in, out)
* Convert_BYTE_TO_SINT(in, out)
* Convert_BYTE_TO_STRING(in, out)
* Convert_BYTE_TO_TIME(in, out)
* Convert_BYTE_TO_TOD(in, out)
* Convert_BYTE_TO_UDINT(in, out)
* Convert_BYTE_TO_UINT(in, out)
* Convert_BYTE_TO_ULINT(in, out)
* Convert_BYTE_TO_USINT(in, out)
* Convert_BYTE_TO_WORD(in, out)
* Convert_DATE_TO_BOOL(in, out)
* Convert_DATE_TO_BYTE(in, out)
* Convert_DATE_TO_DATE(in, out)
* Convert_DATE_TO_DINT(in, out)
* Convert_DATE_TO_DT(in, out)
* Convert_DATE_TO_DWORD(in, out)
* Convert_DATE_TO_INT(in, out)
* Convert_DATE_TO_LINT(in, out)
* Convert_DATE_TO_LREAL(in, out)
* Convert_DATE_TO_LWORD(in, out)
* Convert_DATE_TO_REAL(in, out)
* Convert_DATE_TO_SINT(in, out)
* Convert_DATE_TO_STRING(in, out)
* Convert_DATE_TO_TIME(in, out)
* Convert_DATE_TO_TOD(in, out)
* Convert_DATE_TO_UDINT(in, out)
* Convert_DATE_TO_UINT(in, out)
* Convert_DATE_TO_ULINT(in, out)
* Convert_DATE_TO_USINT(in, out)
* Convert_DATE_TO_WORD(in, out)
* Convert_DINT_TO_BOOL(in, out)
* Convert_DINT_TO_BYTE(in, out)
* Convert_DINT_TO_DATE(in, out)
* Convert_DINT_TO_DINT(in, out)
* Convert_DINT_TO_DT(in, out)
* Convert_DINT_TO_DWORD(in, out)
* Convert_DINT_TO_INT(in, out)
* Convert_DINT_TO_LINT(in, out)
* Convert_DINT_TO_LREAL(in, out)
* Convert_DINT_TO_LWORD(in, out)
* Convert_DINT_TO_REAL(in, out)
* Convert_DINT_TO_SINT(in, out)
* Convert_DINT_TO_STRING(in, out)
* Convert_DINT_TO_TIME(in, out)
* Convert_DINT_TO_TOD(in, out)
* Convert_DINT_TO_UDINT(in, out)
* Convert_DINT_TO_UINT(in, out)
* Convert_DINT_TO_ULINT(in, out)
* Convert_DINT_TO_USINT(in, out)
* Convert_DINT_TO_WORD(in, out)
* Convert_DT_TO_BOOL(in, out)
* Convert_DT_TO_BYTE(in, out)
* Convert_DT_TO_DATE(in, out)
* Convert_DT_TO_DINT(in, out)
* Convert_DT_TO_DT(in, out)
* Convert_DT_TO_DWORD(in, out)
* Convert_DT_TO_INT(in, out)
* Convert_DT_TO_LINT(in, out)
* Convert_DT_TO_LREAL(in, out)
* Convert_DT_TO_LWORD(in, out)
* Convert_DT_TO_REAL(in, out)
* Convert_DT_TO_SINT(in, out)
* Convert_DT_TO_STRING(in, out)
* Convert_DT_TO_TIME(in, out)
* Convert_DT_TO_TOD(in, out)
* Convert_DT_TO_UDINT(in, out)
* Convert_DT_TO_UINT(in, out)
* Convert_DT_TO_ULINT(in, out)
* Convert_DT_TO_USINT(in, out)
* Convert_DT_TO_WORD(in, out)
* Convert_DWORD_TO_BOOL(in, out)
* Convert_DWORD_TO_BYTE(in, out)
* Convert_DWORD_TO_DATE(in, out)
* Convert_DWORD_TO_DINT(in, out)
* Convert_DWORD_TO_DT(in, out)
* Convert_DWORD_TO_DWORD(in, out)
* Convert_DWORD_TO_INT(in, out)
* Convert_DWORD_TO_LINT(in, out)
* Convert_DWORD_TO_LREAL(in, out)
* Convert_DWORD_TO_LWORD(in, out)
* Convert_DWORD_TO_REAL(in, out)
* Convert_DWORD_TO_SINT(in, out)
* Convert_DWORD_TO_STRING(in, out)
* Convert_DWORD_TO_TIME(in, out)
* Convert_DWORD_TO_TOD(in, out)
* Convert_DWORD_TO_UDINT(in, out)
* Convert_DWORD_TO_UINT(in, out)
* Convert_DWORD_TO_ULINT(in, out)
* Convert_DWORD_TO_USINT(in, out)
* Convert_DWORD_TO_WORD(in, out)
* Convert_INT_TO_BOOL(in, out)
* Convert_INT_TO_BYTE(in, out)
* Convert_INT_TO_DATE(in, out)
* Convert_INT_TO_DINT(in, out)
* Convert_INT_TO_DT(in, out)
* Convert_INT_TO_DWORD(in, out)
* Convert_INT_TO_INT(in, out)
* Convert_INT_TO_LINT(in, out)
* Convert_INT_TO_LREAL(in, out)
* Convert_INT_TO_LWORD(in, out)
* Convert_INT_TO_REAL(in, out)
* Convert_INT_TO_SINT(in, out)
* Convert_INT_TO_STRING(in, out)
* Convert_INT_TO_TIME(in, out)
* Convert_INT_TO_TOD(in, out)
* Convert_INT_TO_UDINT(in, out)
* Convert_INT_TO_UINT(in, out)
* Convert_INT_TO_ULINT(in, out)
* Convert_INT_TO_USINT(in, out)
* Convert_INT_TO_WORD(in, out)
* Convert_LINT_TO_BOOL(in, out)
* Convert_LINT_TO_BYTE(in, out)
* Convert_LINT_TO_DATE(in, out)
* Convert_LINT_TO_DINT(in, out)
* Convert_LINT_TO_DT(in, out)
* Convert_LINT_TO_DWORD(in, out)
* Convert_LINT_TO_INT(in, out)
* Convert_LINT_TO_LINT(in, out)
* Convert_LINT_TO_LREAL(in, out)
* Convert_LINT_TO_LWORD(in, out)
* Convert_LINT_TO_REAL(in, out)
* Convert_LINT_TO_SINT(in, out)
* Convert_LINT_TO_STRING(in, out)
* Convert_LINT_TO_TIME(in, out)
* Convert_LINT_TO_TOD(in, out)
* Convert_LINT_TO_UDINT(in, out)
* Convert_LINT_TO_UINT(in, out)
* Convert_LINT_TO_ULINT(in, out)
* Convert_LINT_TO_USINT(in, out)
* Convert_LINT_TO_WORD(in, out)
* Convert_LREAL_TO_BOOL(in, out)
* Convert_LREAL_TO_BYTE(in, out)
* Convert_LREAL_TO_DATE(in, out)
* Convert_LREAL_TO_DINT(in, out)
* Convert_LREAL_TO_DT(in, out)
* Convert_LREAL_TO_DWORD(in, out)
* Convert_LREAL_TO_INT(in, out)
* Convert_LREAL_TO_LINT(in, out)
* Convert_LREAL_TO_LREAL(in, out)
* Convert_LREAL_TO_LWORD(in, out)
* Convert_LREAL_TO_REAL(in, out)
* Convert_LREAL_TO_SINT(in, out)
* Convert_LREAL_TO_STRING(in, out)
* Convert_LREAL_TO_TIME(in, out)
* Convert_LREAL_TO_TOD(in, out)
* Convert_LREAL_TO_UDINT(in, out)
* Convert_LREAL_TO_UINT(in, out)
* Convert_LREAL_TO_ULINT(in, out)
* Convert_LREAL_TO_USINT(in, out)
* Convert_LREAL_TO_WORD(in, out)
* Convert_LWORD_TO_BOOL(in, out)
* Convert_LWORD_TO_BYTE(in, out)
* Convert_LWORD_TO_DATE(in, out)
* Convert_LWORD_TO_DINT(in, out)
* Convert_LWORD_TO_DT(in, out)
* Convert_LWORD_TO_DWORD(in, out)
* Convert_LWORD_TO_INT(in, out)
* Convert_LWORD_TO_LINT(in, out)
* Convert_LWORD_TO_LREAL(in, out)
* Convert_LWORD_TO_LWORD(in, out)
* Convert_LWORD_TO_REAL(in, out)
* Convert_LWORD_TO_SINT(in, out)
* Convert_LWORD_TO_STRING(in, out)
* Convert_LWORD_TO_TIME(in, out)
* Convert_LWORD_TO_TOD(in, out)
* Convert_LWORD_TO_UDINT(in, out)
* Convert_LWORD_TO_UINT(in, out)
* Convert_LWORD_TO_ULINT(in, out)
* Convert_LWORD_TO_USINT(in, out)
* Convert_LWORD_TO_WORD(in, out)
* Convert_REAL_TO_BOOL(in, out)
* Convert_REAL_TO_BYTE(in, out)
* Convert_REAL_TO_DATE(in, out)
* Convert_REAL_TO_DINT(in, out)
* Convert_REAL_TO_DT(in, out)
* Convert_REAL_TO_DWORD(in, out)
* Convert_REAL_TO_INT(in, out)
* Convert_REAL_TO_LINT(in, out)
* Convert_REAL_TO_LREAL(in, out)
* Convert_REAL_TO_LWORD(in, out)
* Convert_REAL_TO_REAL(in, out)
* Convert_REAL_TO_SINT(in, out)
* Convert_REAL_TO_STRING(in, out)
* Convert_REAL_TO_TIME(in, out)
* Convert_REAL_TO_TOD(in, out)
* Convert_REAL_TO_UDINT(in, out)
* Convert_REAL_TO_UINT(in, out)
* Convert_REAL_TO_ULINT(in, out)
* Convert_REAL_TO_USINT(in, out)
* Convert_REAL_TO_WORD(in, out)
* Convert_SINT_TO_BOOL(in, out)
* Convert_SINT_TO_BYTE(in, out)
* Convert_SINT_TO_DATE(in, out)
* Convert_SINT_TO_DINT(in, out)
* Convert_SINT_TO_DT(in, out)
* Convert_SINT_TO_DWORD(in, out)
* Convert_SINT_TO_INT(in, out)
* Convert_SINT_TO_LINT(in, out)
* Convert_SINT_TO_LREAL(in, out)
* Convert_SINT_TO_LWORD(in, out)
* Convert_SINT_TO_REAL(in, out)
* Convert_SINT_TO_SINT(in, out)
* Convert_SINT_TO_STRING(in, out)
* Convert_SINT_TO_TIME(in, out)
* Convert_SINT_TO_TOD(in, out)
* Convert_SINT_TO_UDINT(in, out)
* Convert_SINT_TO_UINT(in, out)
* Convert_SINT_TO_ULINT(in, out)
* Convert_SINT_TO_USINT(in, out)
* Convert_SINT_TO_WORD(in, out)
* Convert_STRING_TO_BOOL(in, out)
* Convert_STRING_TO_BYTE(in, out)
* Convert_STRING_TO_DATE(in, out)
* Convert_STRING_TO_DINT(in, out)
* Convert_STRING_TO_DT(in, out)
* Convert_STRING_TO_DWORD(in, out)
* Convert_STRING_TO_INT(in, out)
* Convert_STRING_TO_LINT(in, out)
* Convert_STRING_TO_LREAL(in, out)
* Convert_STRING_TO_LWORD(in, out)
* Convert_STRING_TO_REAL(in, out)
* Convert_STRING_TO_SINT(in, out)
* Convert_STRING_TO_STRING(in, out)
* Convert_STRING_TO_TIME(in, out)
* Convert_STRING_TO_TOD(in, out)
* Convert_STRING_TO_UDINT(in, out)
* Convert_STRING_TO_UINT(in, out)
* Convert_STRING_TO_ULINT(in, out)
* Convert_STRING_TO_USINT(in, out)
* Convert_STRING_TO_WORD(in, out)
* Convert_TIME_TO_BOOL(in, out)
* Convert_TIME_TO_BYTE(in, out)
* Convert_TIME_TO_DATE(in, out)
* Convert_TIME_TO_DINT(in, out)
* Convert_TIME_TO_DT(in, out)
* Convert_TIME_TO_DWORD(in, out)
* Convert_TIME_TO_INT(in, out)
* Convert_TIME_TO_LINT(in, out)
* Convert_TIME_TO_LREAL(in, out)
* Convert_TIME_TO_LWORD(in, out)
* Convert_TIME_TO_REAL(in, out)
* Convert_TIME_TO_SINT(in, out)
* Convert_TIME_TO_STRING(in, out)
* Convert_TIME_TO_TIME(in, out)
* Convert_TIME_TO_TOD(in, out)
* Convert_TIME_TO_UDINT(in, out)
* Convert_TIME_TO_UINT(in, out)
* Convert_TIME_TO_ULINT(in, out)
* Convert_TIME_TO_USINT(in, out)
* Convert_TIME_TO_WORD(in, out)
* Convert_TOD_TO_BOOL(in, out)
* Convert_TOD_TO_BYTE(in, out)
* Convert_TOD_TO_DATE(in, out)
* Convert_TOD_TO_DINT(in, out)
* Convert_TOD_TO_DT(in, out)
* Convert_TOD_TO_DWORD(in, out)
* Convert_TOD_TO_INT(in, out)
* Convert_TOD_TO_LINT(in, out)
* Convert_TOD_TO_LREAL(in, out)
* Convert_TOD_TO_LWORD(in, out)
* Convert_TOD_TO_REAL(in, out)
* Convert_TOD_TO_SINT(in, out)
* Convert_TOD_TO_STRING(in, out)
* Convert_TOD_TO_TIME(in, out)
* Convert_TOD_TO_TOD(in, out)
* Convert_TOD_TO_UDINT(in, out)
* Convert_TOD_TO_UINT(in, out)
* Convert_TOD_TO_ULINT(in, out)
* Convert_TOD_TO_USINT(in, out)
* Convert_TOD_TO_WORD(in, out)
* Convert_UDINT_TO_BOOL(in, out)
* Convert_UDINT_TO_BYTE(in, out)
* Convert_UDINT_TO_DATE(in, out)
* Convert_UDINT_TO_DINT(in, out)
* Convert_UDINT_TO_DT(in, out)
* Convert_UDINT_TO_DWORD(in, out)
* Convert_UDINT_TO_INT(in, out)
* Convert_UDINT_TO_LINT(in, out)
* Convert_UDINT_TO_LREAL(in, out)
* Convert_UDINT_TO_LWORD(in, out)
* Convert_UDINT_TO_REAL(in, out)
* Convert_UDINT_TO_SINT(in, out)
* Convert_UDINT_TO_STRING(in, out)
* Convert_UDINT_TO_TIME(in, out)
* Convert_UDINT_TO_TOD(in, out)
* Convert_UDINT_TO_UDINT(in, out)
* Convert_UDINT_TO_UINT(in, out)
* Convert_UDINT_TO_ULINT(in, out)
* Convert_UDINT_TO_USINT(in, out)
* Convert_UDINT_TO_WORD(in, out)
* Convert_UINT_TO_BOOL(in, out)
* Convert_UINT_TO_BYTE(in, out)
* Convert_UINT_TO_DATE(in, out)
* Convert_UINT_TO_DINT(in, out)
* Convert_UINT_TO_DT(in, out)
* Convert_UINT_TO_DWORD(in, out)
* Convert_UINT_TO_INT(in, out)
* Convert_UINT_TO_LINT(in, out)
* Convert_UINT_TO_LREAL(in, out)
* Convert_UINT_TO_LWORD(in, out)
* Convert_UINT_TO_REAL(in, out)
* Convert_UINT_TO_SINT(in, out)
* Convert_UINT_TO_STRING(in, out)
* Convert_UINT_TO_TIME(in, out)
* Convert_UINT_TO_TOD(in, out)
* Convert_UINT_TO_UDINT(in, out)
* Convert_UINT_TO_UINT(in, out)
* Convert_UINT_TO_ULINT(in, out)
* Convert_UINT_TO_USINT(in, out)
* Convert_UINT_TO_WORD(in, out)
* Convert_ULINT_TO_BOOL(in, out)
* Convert_ULINT_TO_BYTE(in, out)
* Convert_ULINT_TO_DATE(in, out)
* Convert_ULINT_TO_DINT(in, out)
* Convert_ULINT_TO_DT(in, out)
* Convert_ULINT_TO_DWORD(in, out)
* Convert_ULINT_TO_INT(in, out)
* Convert_ULINT_TO_LINT(in, out)
* Convert_ULINT_TO_LREAL(in, out)
* Convert_ULINT_TO_LWORD(in, out)
* Convert_ULINT_TO_REAL(in, out)
* Convert_ULINT_TO_SINT(in, out)
* Convert_ULINT_TO_STRING(in, out)
* Convert_ULINT_TO_TIME(in, out)
* Convert_ULINT_TO_TOD(in, out)
* Convert_ULINT_TO_UDINT(in, out)
* Convert_ULINT_TO_UINT(in, out)
* Convert_ULINT_TO_ULINT(in, out)
* Convert_ULINT_TO_USINT(in, out)
* Convert_ULINT_TO_WORD(in, out)
* Convert_USINT_TO_BOOL(in, out)
* Convert_USINT_TO_BYTE(in, out)
* Convert_USINT_TO_DATE(in, out)
* Convert_USINT_TO_DINT(in, out)
* Convert_USINT_TO_DT(in, out)
* Convert_USINT_TO_DWORD(in, out)
* Convert_USINT_TO_INT(in, out)
* Convert_USINT_TO_LINT(in, out)
* Convert_USINT_TO_LREAL(in, out)
* Convert_USINT_TO_LWORD(in, out)
* Convert_USINT_TO_REAL(in, out)
* Convert_USINT_TO_SINT(in, out)
* Convert_USINT_TO_STRING(in, out)
* Convert_USINT_TO_TIME(in, out)
* Convert_USINT_TO_TOD(in, out)
* Convert_USINT_TO_UDINT(in, out)
* Convert_USINT_TO_UINT(in, out)
* Convert_USINT_TO_ULINT(in, out)
* Convert_USINT_TO_USINT(in, out)
* Convert_USINT_TO_WORD(in, out)
* Convert_WORD_TO_BOOL(in, out)
* Convert_WORD_TO_BYTE(in, out)
* Convert_WORD_TO_DATE(in, out)
* Convert_WORD_TO_DINT(in, out)
* Convert_WORD_TO_DT(in, out)
* Convert_WORD_TO_DWORD(in, out)
* Convert_WORD_TO_INT(in, out)
* Convert_WORD_TO_LINT(in, out)
* Convert_WORD_TO_LREAL(in, out)
* Convert_WORD_TO_LWORD(in, out)
* Convert_WORD_TO_REAL(in, out)
* Convert_WORD_TO_SINT(in, out)
* Convert_WORD_TO_STRING(in, out)
* Convert_WORD_TO_TIME(in, out)
* Convert_WORD_TO_TOD(in, out)
* Convert_WORD_TO_UDINT(in, out)
* Convert_WORD_TO_UINT(in, out)
* Convert_WORD_TO_ULINT(in, out)
* Convert_WORD_TO_USINT(in, out)
* Convert_WORD_TO_WORD(in, out)