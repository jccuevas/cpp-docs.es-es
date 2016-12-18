---
title: "localeconv | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "localeconv"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "localeconv"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "lconv (tipo)"
  - "localeconv (función)"
  - "configuraciones regionales, obtener información sobre"
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# localeconv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recopila información detallada en las configuraciones regionales.  
  
## Sintaxis  
  
```  
  
struct lconv *localeconv( void );  
```  
  
## Valor devuelto  
 `localeconv` devuelve un puntero a rellenar\- del objeto de [lconv struct](../../c-runtime-library/standard-types.md)escrito.  Los valores contenidos en el objeto se pueden sobrescribir por llamadas posteriores a `localeconv` y sin modificar directamente el objeto.  Las llamadas a [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) con los valores de `category` de `LC_ALL`, de `LC_MONETARY`, o de `LC_NUMERIC` sobrescriben el contenido de la estructura.  
  
## Comentarios  
 La función de `localeconv` recopila información detallada sobre el formato numérico para la configuración regional actual.  Esta información se almacena en una estructura de **lconv**escrito.  La estructura de **lconv** , definido en LOCALE.H, contiene los miembros siguientes:  
  
 `char *decimal_point, wchar_t *_W_decimal_point`  
 Carácter de separador decimal para cantidades no monetarias.  
  
 `char *thousands_sep, wchar_t *_W_thousands_sep`  
 Carácter que separa los grupos de dígitos a la izquierda del separador decimal para cantidades no monetarias.  
  
 `char *grouping`  
 Tamaño de cada grupo de dígitos en cantidades no monetarias.  
  
 `char *int_curr_symbol, wchar_t *_W_int_curr_symbol`  
 Símbolo de divisa internacional para la configuración regional actual.  Los tres primeros caracteres especifican el símbolo de divisa internacional alfabético definido en *ISO 4217 códigos para la Representación* del estándar de divisa y de Funds.  El cuarto carácter \(inmediatamente antes del carácter null\) separa el símbolo de divisa internacional de cantidad monetaria.  
  
 `char *currency_symbol, wchar_t *_W_currency_symbol`  
 Símbolo de moneda local para la configuración regional actual.  
  
 `char *mon_decimal_point, wchar_t *_W_mon_decimal_point`  
 Carácter de separador decimal para cantidades de moneda.  
  
 `char *mon_thousands_sep, wchar_t *_W_mon_thousands_sep`  
 Separador de grupos de dígitos a la izquierda de la posición decimal en cantidades de moneda.  
  
 `char *mon_grouping`  
 Tamaño de cada grupo de dígitos en cantidades de moneda.  
  
 `char *positive_sign, wchar_t *_W_positive_sign`  
 Cadena que indica el signo para cantidades de moneda no negativa.  
  
 `char *negative_sign, wchar_t *_W_negative_sign`  
 Cadena que indica el signo para cantidades de moneda negativas.  
  
 `char int_frac_digits`  
 Número de dígitos a la derecha del separador decimal en cantidades monetarias internacionalmente con formato.  
  
 `char frac_digits`  
 Número de dígitos a la derecha del separador decimal en cantidades de moneda con formato.  
  
 `char p_cs_precedes`  
 Establezca en 1 si el símbolo de divisa precede el valor para la cantidad monetaria con formato no negativa.  Establezca en 0 si el símbolo sigue valor.  
  
 `char p_sep_by_space`  
 Establezca en 1 si el símbolo de moneda está separado por el espacio del valor de la cantidad monetaria con formato no negativa.  Establezca en 0 si no hay separación de espacio.  
  
 `char n_cs_precedes`  
 Establezca en 1 si el símbolo de divisa precede el valor para la cantidad monetaria con formato negativa.  Establezca en 0 si el token tiene éxito valor.  
  
 `char n_sep_by_space`  
 Establezca en 1 si el símbolo de moneda está separado por el espacio del valor de la cantidad monetaria con formato negativa.  Establezca en 0 si no hay separación de espacio.  
  
 `char p_sign_posn`  
 Posición de signo positivo en cantidades de moneda con formato no negativa.  
  
 `char n_sign_posn`  
 La posición del signo positivo en negativa formateó cantidades de moneda.  
  
 Los miembros de la estructura que tienen `char` `*` y versiones de `wchar_t *` son punteros a cadenas.  Cualquiera de estos ese equals `""` \(o `L""` para `wchar_t *`\) tiene una longitud cero o no se admite en la configuración regional actual.  Observe que `decimal_point` y `_W_decimal_point` se admiten siempre y de longitud cero.  
  
 Los miembros de `char` de estructura son pequeños números no negativos, pero no caracteres.  Cualquiera de estos ese equals **CHAR\_MAX** no se admite en la configuración regional actual.  
  
 Los elementos de **grouping** y de **mon\_grouping** se interpretan según las reglas siguientes.  
  
 **CHAR\_MAX**  
 No realice cualquier agrupación posterior.  
  
 0  
 Utilice el elemento anterior para cada uno de dígitos restantes.  
  
 *n*  
 Número de dígitos que constituyen el grupo actual.  El elemento siguiente se examina para determinar el tamaño del siguiente grupo de dígitos antes de que lo actual agrupar.  
  
 Los valores para **int\_curr\_symbol** se interpretan según las reglas siguientes:  
  
-   Los tres primeros caracteres especifican el símbolo de divisa internacional alfabético definido en *ISO 4217 códigos para la Representación del estándar de divisa y de Funds* .  
  
-   El cuarto carácter \(inmediatamente antes del carácter null\) separa el símbolo de divisa internacional de cantidad monetaria.  
  
 Los valores para **p\_cs\_precedes** y **n\_cs\_precedes** se interpretan según las reglas siguientes \(la regla de **n\_cs\_precedes** está entre paréntesis\):  
  
 0  
 El símbolo de divisa sigue el valor por valor monetario con formato \(negativo\) no negativo.  
  
 1  
 El símbolo de divisa precede el valor por valor monetario con formato \(negativo\) no negativo.  
  
 Los valores para **p\_sep\_by\_space** y **n\_sep\_by\_space** se interpretan según las reglas siguientes \(la regla de **n\_sep\_by\_space** está entre paréntesis\):  
  
 0  
 El símbolo de moneda es independiente de valor por espacio por valor monetario con formato \(negativo\) no negativo.  
  
 1  
 No hay separación de espacio entre el símbolo de moneda y el valor por valor monetario con formato \(negativo\) no negativo.  
  
 Los valores para **p\_sign\_posn** y **n\_sign\_posn** se interpretan según las reglas siguientes:  
  
 0  
 Cantidad y símbolo de divisa de anillo de paréntesis.  
  
 1  
 La cadena de signo precede cantidad y el símbolo de moneda.  
  
 2  
 La cadena de signo sigue cantidad y el símbolo de moneda.  
  
 3  
 La cadena de signo inmediatamente delante del símbolo de moneda.  
  
 4  
 La cadena de signo sigue inmediatamente al símbolo de divisa.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`localeconv`|\<locale.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Vea también  
 [Configuración regional](../../c-runtime-library/locale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [strftime, wcsftime, \_strftime\_l, \_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm, wcsxfrm, \_strxfrm\_l, \_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)