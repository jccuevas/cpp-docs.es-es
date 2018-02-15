---
title: vfscanf, vfwscanf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- vfwscanf
- vfscanf
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- vfwscanf
- _vftscanf
- vfscanf
dev_langs:
- C++
ms.assetid: c06450ef-03f1-4d24-a8ac-d2dd98847918
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e3cbf345f686a08fbcd7e3ead6ebcd24d9cd803
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="vfscanf-vfwscanf"></a>vfscanf, vfwscanf
Lee datos con formato de un flujo. Hay disponibles versiones más seguras de estas funciones; vea [vfscanf_s, vfwscanf_s](../../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int vfscanf(   
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int vfwscanf(   
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura `FILE` .  
  
 `format`  
 Cadena de control de formato.  
  
 `arglist`  
 Lista de argumentos de variable.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos leídos pero no asignados. Un valor devuelto de 0 indica que no se ha asignado ningún campo. Si se produce un error, o si se llega al final del flujo de archivo antes de la primera conversión, el valor devuelto es `EOF` para `vfscanf` y `vfwscanf`.  
  
 Estas funciones validan sus parámetros. Si `stream` o `format` es un puntero nulo, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `vfscanf` lee datos de la posición actual de `stream` en las ubicaciones que proporciona la lista de argumentos `arglist`. Cada argumento de la lista debe ser un puntero a una variable de un tipo que se corresponda con un especificador de tipo en `format`. `format` controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento `format` de `scanf`. Vea [scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) para obtener una descripción de `format`.  
  
 `vfwscanf` es una versión con caracteres anchos de `vfscanf`; el argumento de formato para `vfwscanf` es una cadena de caracteres anchos. Estas funciones se comportan igual si el flujo se abre en modo ANSI. `vfscanf` no admite la entrada desde un flujo UNICODE.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftscanf`|`vfscanf`|`vfscanf`|`vfwscanf`|  
  
 Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`vfscanf`|\<stdio.h>|  
|`vfwscanf`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_vfscanf.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses vfscanf to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
FILE *stream;  
  
int call_vfscanf(FILE * istream, char * format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vfscanf(istream, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main(void)  
{  
    long l;  
    float fp;  
    char s[81];  
    char c;  
  
    if (fopen_s(&stream, "vfscanf.out", "w+") != 0)  
    {  
        printf("The file vfscanf.out was not opened\n");  
    }  
    else  
    {  
        fprintf(stream, "%s %ld %f%c", "a-string",  
            65000, 3.14159, 'x');  
        // Security caution!  
        // Beware loading data from a file without confirming its size,  
        // as it may lead to a buffer overrun situation.  
  
        // Set pointer to beginning of file:  
        fseek(stream, 0L, SEEK_SET);  
  
        // Read data back from file:  
        call_vfscanf(stream, "%s %ld %f%c", s, &l, &fp, &c);  
  
        // Output data read:   
        printf("%s\n", s);  
        printf("%ld\n", l);  
        printf("%f\n", fp);  
        printf("%c\n", c);  
  
        fclose(stream);  
    }  
}  
  
```  
  
```Output  
a-string  
65000  
3.141590  
x  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf, _fprintf_l, fwprintf, _fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [scanf, _scanf_l, wscanf, _wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, _sscanf_l, swscanf, _swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)   
 [vfscanf_s, vfwscanf_s](../../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)