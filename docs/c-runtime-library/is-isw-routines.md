---
title: is, isw (Rutinas) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- isw
- is
dev_langs:
- C++
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa1cc76bf925a334b78e5f15565c089081cfe9d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="is-isw-routines"></a>is, isw (Rutinas)
|||  
|-|-|  
|[isalnum, iswalnum, _isalnum_l, _iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph, iswgraph, _isgraph_l, _iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|  
|[isalpha, iswalpha, _isalpha_l, _iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|  
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower, iswlower, _islower_l, _iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|  
|[isblank, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint, iswprint, _isprint_l, _iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|  
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct, iswpunct, _ispunct_l, _iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|  
|[iscsym, iscsymf, __iscsym, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|[isspace, iswspace, _isspace_l, _iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|  
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper, _isupper_l, iswupper, _iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|  
|[isdigit, iswdigit, _isdigit_l, _iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|  
  
## <a name="remarks"></a>Comentarios  
 Estas rutinas comprueban si los caracteres cumplen las condiciones especificadas.  
  
 Las rutinas **is** producen resultados significativos para cualquier argumento de entero de -1 (`EOF`) a **UCHAR_MAX** (0xFF), incluidos. El tipo de argumento esperado es `int`.  
  
> [!CAUTION]
>  En el caso de las rutinas **is**, al pasar un argumento de tipo `char`, se podrían producir resultados imprevisibles. Un carácter de un solo byte de SBCS o MBCS de tipo `char` con un valor mayor que 0x7F es negativo. Si se pasa `char`, el compilador puede convertir el valor en un `int` con signo o un **long** con signo. El compilador puede agregar a este valor la extensión de signo, lo que provocaría resultados inesperados.  
  
 Las rutinas **isw** producen resultados negativos para cualquier valor entero de -1 (**WEOF**) a 0xFFFF, incluidos. El tipo de datos **wint_t** se define en WCHAR.H como **unsigned short**; puede contener cualquier carácter ancho o el valor de final de archivo de caracteres anchos (**WEOF**).  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa.  
  
 En la configuración regional "C", las condiciones de prueba de las rutinas **is** son las siguientes:  
  
 `isalnum`  
 Alfanumérico (A - Z, a - z o 0 - 9).  
  
 `isalpha`  
 Alfabético (A - Z o a - z).  
  
 `__isascii`  
 Carácter ASCII (0x00 - 0x7F).  
  
 `isblank`  
 Tabulación horizontal o carácter de espacio (0x09 o 0x20).  
  
 `iscntrl`  
 Carácter de control (0x00 - 0x1F o 0x7F).  
  
 `__iscsym`  
 Letra, carácter de subrayado o dígito.  
  
 `__iscsymf`  
 Letra o carácter de subrayado.  
  
 **isdigit**  
 Dígito decimal (0 - 9).  
  
 `isgraph`  
 Un carácter imprimible excepto el espacio ( ).  
  
 `islower`  
 Minúscula (a - z).  
  
 `isprint`  
 Carácter imprimible incluido el espacio (0x20 - 0x7E).  
  
 `ispunct`  
 Carácter de puntuación.  
  
 `isspace`  
 Carácter de espacio en blanco (0x09 - 0x0D o 0x20).  
  
 `isupper`  
 Mayúscula (A - Z).  
  
 `isxdigit`  
 Dígito hexadecimal (A - F, a - f o 0 - 9).  
  
 En el caso de las rutinas **isw**, el resultado de prueba de la condición especificada es independiente de la configuración regional. Las condiciones de prueba de las funciones **isw** son las siguientes:  
  
 `iswalnum`  
 `iswalpha` o `iswdigit`.  
  
 `iswalpha`  
 Cualquier carácter ancho que pertenezca a un conjunto que se define en la implementación para el que ni `iswcntrl`, ni `iswdigit`, ni `iswpunct` ni `iswspace` sea distinto de cero. `iswalpha` devuelve un valor distinto de cero solo para caracteres anchos para los que `iswupper` o `iswlower` sea distinto de cero.  
  
 `iswascii`  
 Representación de carácter ancho de caracteres ASCII (0x0000 - 0x007F).  
  
 `iswblank`  
 Carácter ancho correspondiente al carácter de espacio estándar o que pertenece a un conjunto de caracteres anchos que se define en la implementación para los que `iswalnum` es FALSE. Los caracteres en blanco estándar son el espacio (L' ') y la tabulación horizontal (L'\t').  
  
 `iswcntrl`  
 Carácter ancho de control.  
  
 **__iswcsym**  
 Cualquier carácter ancho para el que **isalnum** sea True, o el carácter '_'.  
  
 **__iswcsymf**  
 Cualquier carácter ancho para el que `iswalpha` sea True, o el carácter '_'.  
  
 `iswctype`  
 El carácter tiene la propiedad especificada por el argumento `desc`. Por cada valor válido del argumento `desc` de `iswctype`, hay una rutina equivalente de clasificación de carácter ancho, como se muestra en la tabla siguiente:  
  
 **Equivalencia de iswctype(**   
 ***c, desc*) con otras rutinas de prueba de isw**  
  
|Valor del argumento *desc*|equivalente de iswctype( *c, desc* )|  
|------------------------------|----------------------------------------|  
|**_ALPHA**|**iswalpha(** `c` **)**|  
|**_ALPHA** &#124; **_DIGIT**|**iswalnum(** `c` **)**|  
|**_BLANK**|**iswblank(** `c` **)**|  
|**_CONTROL**|**iswcntrl(** `c` **)**|  
|**_DIGIT**|**iswdigit(** `c` **)**|  
|**_ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph(** `c` **)**|  
|**_LOWER**|**iswlower(** `c` **)**|  
|**_ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint(** `c` **)**|  
|**_PUNCT**|**iswpunct(** `c` **)**|  
|**_BLANK**|**iswblank(** `c` **)**|  
|**_SPACE**|**iswspace(** `c` **)**|  
|**_UPPER**|**iswupper(** `c` **)**|  
|**_HEX**|**iswxdigit(** `c` **)**|  
  
 `iswdigit`  
 Carácter ancho correspondiente a un carácter de dígito decimal.  
  
 `iswgraph`  
 Carácter ancho imprimible excepto el carácter ancho de espacio (L' ').  
  
 `iswlower`  
 Minúscula, o una de un conjunto de caracteres anchos que se define en la implementación para los que ni `iswcntrl`, ni `iswdigit`, ni `iswpunct` ni `iswspace` es distinto de cero. `iswlower` devuelve un valor distinto de cero solo para los caracteres anchos que corresponden a minúsculas.  
  
 `iswprint`  
 Carácter ancho imprimible incluido el carácter ancho de espacio (L' ').  
  
 `iswpunct`  
 Carácter ancho imprimible que no es ni el carácter ancho de espacio (L' ') ni un carácter ancho para el que `iswalnum` sea distinto de cero.  
  
 `iswspace`  
 Carácter ancho correspondiente al carácter de espacio en blanco estándar o que pertenece a un conjunto de caracteres anchos que se define en la implementación para los que `iswalnum` es FALSE. Los caracteres de espacio en blanco estándar son: espacio (L' '), avance de página (L'\f'), nueva línea (L'\n'), retorno de carro (L'\r'), tabulación horizontal (L'\t') y tabulación vertical (L'\v').  
  
 `iswupper`  
 Carácter ancho que es una mayúscula o que pertenece a un conjunto de caracteres anchos definido en la implementación para los que ni `iswcntrl`, ni `iswdigit`, ni `iswpunct`, ni `iswspace` sea distinto de cero. `iswupper` devuelve un valor distinto de cero solo para los caracteres anchos que corresponden a mayúsculas.  
  
 `iswxdigit`  
 Carácter ancho que corresponde a un carácter de dígito hexadecimal.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_isfam.c  
/* This program tests all characters between 0x0  
 * and 0x7F, then displays each character with abbreviations  
 * for the character-type codes that apply.  
 */  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   for( ch = 0; ch <= 0x7F; ch++ )  
   {  
      printf( "%.2x  ", ch );  
      printf( " %c", isprint( ch )  ? ch   : ' ' );  
      printf( "%4s", isalnum( ch )  ? "AN" : "" );  
      printf( "%3s", isalpha( ch )  ? "A"  : "" );  
      printf( "%3s", __isascii( ch )  ? "AS" : "" );  
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );  
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );  
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );  
      printf( "%3s", isdigit( ch )  ? "D"  : "" );  
      printf( "%3s", isgraph( ch )  ? "G"  : "" );  
      printf( "%3s", islower( ch )  ? "L"  : "" );  
      printf( "%3s", ispunct( ch )  ? "PU" : "" );  
      printf( "%3s", isspace( ch )  ? "S"  : "" );  
      printf( "%3s", isprint( ch )  ? "PR" : "" );  
      printf( "%3s", isupper( ch )  ? "U"  : "" );  
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );  
      printf( ".\n" );  
   }  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
00            AS  C                              .  
01            AS  C                              .  
02            AS  C                              .  
03            AS  C                              .  
04            AS  C                              .  
05            AS  C                              .  
06            AS  C                              .  
07            AS  C                              .  
08            AS  C                              .  
09            AS  C                    S         .  
0a            AS  C                    S         .  
0b            AS  C                    S         .  
0c            AS  C                    S         .  
0d            AS  C                    S         .  
0e            AS  C                              .  
0f            AS  C                              .  
10            AS  C                              .  
11            AS  C                              .  
12            AS  C                              .  
13            AS  C                              .  
14            AS  C                              .  
15            AS  C                              .  
16            AS  C                              .  
17            AS  C                              .  
18            AS  C                              .  
19            AS  C                              .  
1a            AS  C                              .  
1b            AS  C                              .  
1c            AS  C                              .  
1d            AS  C                              .  
1e            AS  C                              .  
1f            AS  C                              .  
20            AS                       S PR      .  
21   !        AS              G    PU    PR      .  
22   "        AS              G    PU    PR      .  
23   #        AS              G    PU    PR      .  
24   $        AS              G    PU    PR      .  
25   %        AS              G    PU    PR      .  
26   &        AS              G    PU    PR      .  
27   '        AS              G    PU    PR      .  
28   (        AS              G    PU    PR      .  
29   )        AS              G    PU    PR      .  
2a   *        AS              G    PU    PR      .  
2b   +        AS              G    PU    PR      .  
2c   ,        AS              G    PU    PR      .  
2d   -        AS              G    PU    PR      .  
2e   .        AS              G    PU    PR      .  
2f   /        AS              G    PU    PR      .  
30   0  AN    AS   CS      D  G          PR     X.  
31   1  AN    AS   CS      D  G          PR     X.  
32   2  AN    AS   CS      D  G          PR     X.  
33   3  AN    AS   CS      D  G          PR     X.  
34   4  AN    AS   CS      D  G          PR     X.  
35   5  AN    AS   CS      D  G          PR     X.  
36   6  AN    AS   CS      D  G          PR     X.  
37   7  AN    AS   CS      D  G          PR     X.  
38   8  AN    AS   CS      D  G          PR     X.  
39   9  AN    AS   CS      D  G          PR     X.  
3a   :        AS              G    PU    PR      .  
3b   ;        AS              G    PU    PR      .  
3c   <        AS              G    PU    PR      .  
3d   =        AS              G    PU    PR      .  
3e   >        AS              G    PU    PR      .  
3f   ?        AS              G    PU    PR      .  
40   @        AS              G    PU    PR      .  
41   A  AN  A AS   CS CSF     G          PR  U  X.  
42   B  AN  A AS   CS CSF     G          PR  U  X.  
43   C  AN  A AS   CS CSF     G          PR  U  X.  
44   D  AN  A AS   CS CSF     G          PR  U  X.  
45   E  AN  A AS   CS CSF     G          PR  U  X.  
46   F  AN  A AS   CS CSF     G          PR  U  X.  
47   G  AN  A AS   CS CSF     G          PR  U   .  
48   H  AN  A AS   CS CSF     G          PR  U   .  
49   I  AN  A AS   CS CSF     G          PR  U   .  
4a   J  AN  A AS   CS CSF     G          PR  U   .  
4b   K  AN  A AS   CS CSF     G          PR  U   .  
4c   L  AN  A AS   CS CSF     G          PR  U   .  
4d   M  AN  A AS   CS CSF     G          PR  U   .  
4e   N  AN  A AS   CS CSF     G          PR  U   .  
4f   O  AN  A AS   CS CSF     G          PR  U   .  
50   P  AN  A AS   CS CSF     G          PR  U   .  
51   Q  AN  A AS   CS CSF     G          PR  U   .  
52   R  AN  A AS   CS CSF     G          PR  U   .  
53   S  AN  A AS   CS CSF     G          PR  U   .  
54   T  AN  A AS   CS CSF     G          PR  U   .  
55   U  AN  A AS   CS CSF     G          PR  U   .  
56   V  AN  A AS   CS CSF     G          PR  U   .  
57   W  AN  A AS   CS CSF     G          PR  U   .  
58   X  AN  A AS   CS CSF     G          PR  U   .  
59   Y  AN  A AS   CS CSF     G          PR  U   .  
5a   Z  AN  A AS   CS CSF     G          PR  U   .  
5b   [        AS              G    PU    PR      .  
5c   \        AS              G    PU    PR      .  
5d   ]        AS              G    PU    PR      .  
5e   ^        AS              G    PU    PR      .  
5f   _        AS   CS CSF     G    PU    PR      .  
60   `        AS              G    PU    PR      .  
61   a  AN  A AS   CS CSF     G  L       PR     X.  
62   b  AN  A AS   CS CSF     G  L       PR     X.  
63   c  AN  A AS   CS CSF     G  L       PR     X.  
64   d  AN  A AS   CS CSF     G  L       PR     X.  
65   e  AN  A AS   CS CSF     G  L       PR     X.  
66   f  AN  A AS   CS CSF     G  L       PR     X.  
67   g  AN  A AS   CS CSF     G  L       PR      .  
68   h  AN  A AS   CS CSF     G  L       PR      .  
69   i  AN  A AS   CS CSF     G  L       PR      .  
6a   j  AN  A AS   CS CSF     G  L       PR      .  
6b   k  AN  A AS   CS CSF     G  L       PR      .  
6c   l  AN  A AS   CS CSF     G  L       PR      .  
6d   m  AN  A AS   CS CSF     G  L       PR      .  
6e   n  AN  A AS   CS CSF     G  L       PR      .  
6f   o  AN  A AS   CS CSF     G  L       PR      .  
70   p  AN  A AS   CS CSF     G  L       PR      .  
71   q  AN  A AS   CS CSF     G  L       PR      .  
72   r  AN  A AS   CS CSF     G  L       PR      .  
73   s  AN  A AS   CS CSF     G  L       PR      .  
74   t  AN  A AS   CS CSF     G  L       PR      .  
75   u  AN  A AS   CS CSF     G  L       PR      .  
76   v  AN  A AS   CS CSF     G  L       PR      .  
77   w  AN  A AS   CS CSF     G  L       PR      .  
78   x  AN  A AS   CS CSF     G  L       PR      .  
79   y  AN  A AS   CS CSF     G  L       PR      .  
7a   z  AN  A AS   CS CSF     G  L       PR      .  
7b   {        AS              G    PU    PR      .  
7c   |        AS              G    PU    PR      .  
7d   }        AS              G    PU    PR      .  
7e   ~        AS              G    PU    PR      .  
7f            AS  C                              .  
```  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de caracteres](../c-runtime-library/character-classification.md)   
 [Configuración regional](../c-runtime-library/locale.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [to (funciones)](../c-runtime-library/to-functions.md)