---
title: Asignaciones de texto genérico en Tchar.h | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7ed29b03a37c9b911a954192152115b1458fd94
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="generic-text-mappings-in-tcharh"></a>Asignaciones de texto genérico en TCHAR.H
Para simplificar la conversión de código para uso internacional, la biblioteca en tiempo de ejecución de [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] proporciona asignaciones de texto genérico específicas de [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] para muchos tipos de datos, rutinas y otros objetos. Se pueden usar estas asignaciones, que están definidas en Tchar.h, para crear código genérico que se puede compilar para juegos de caracteres de un solo byte, multibyte o [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)], en función de la constante de manifiesto que se defina con la instrucción `#define`. Las asignaciones de texto genérico son extensiones de [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] que no son compatibles con [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)].  
  
 Si se usa el archivo Tchar.h, se pueden compilar aplicaciones de un solo byte, de juego de caracteres multibyte (MBCS) y [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] a partir de los mismos códigos fuente. Tchar.h define macros (que tienen el prefijo `_tcs`) que, con las definiciones de preprocesador correctas, se asignan a las funciones `str`, `_mbs` o `wcs`, según proceda. Para compilar MBCS, se ha de definir el símbolo `_MBCS`. Para compilar [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)], se ha de definir el símbolo `_UNICODE`. Para compilar una aplicación de un solo byte, no hay que definir ningún símbolo (opción predeterminada). De forma predeterminada, `_MBCS` está definido para aplicaciones MFC.  
  
 El tipo de datos `_TCHAR` se define de forma condicional en Tchar.h. Si se ha definido el símbolo `_UNICODE` para la compilación, `_TCHAR` se define como `wchar_t`; en caso contrario, para compilaciones MBCS y de un solo byte, se define como `char`. (`wchar_t`, que es el tipo básico de datos de caracteres anchos de Unicode, es el equivalente de 16 bits a un `char` de 8 bits con signo). Para aplicaciones internacionales, se ha de utilizar la familia de funciones `_tcs`, que se ejecuta en unidades `_TCHAR`, no en bytes. Por ejemplo, `_tcsncpy` copias `n` `_TCHARs`, no `n` bytes.  
  
 Dado que algunas funciones de control de cadenas de juego de caracteres de byte único (SBCS) reciben parámetros `char*` (con signo), se genera una advertencia del compilador indicando que el tipo no coincide cuando se define `_MBCS`. Hay tres formas de evitar esta advertencia:  
  
1.  Use fragmentos de código thunk de función inline con seguridad de tipos en Tchar.h. Éste es el comportamiento predeterminado.  
  
2.  Use las macros directas en Tchar.h definiendo `_MB_MAP_DIRECT` en la línea de comandos. Si lo hace, deberá hacer coincidir los tipos manualmente. Este es el método más rápido, pero no garantiza la seguridad de tipos.  
  
3.  Use fragmentos de código thunk de función de biblioteca vinculada estáticamente con seguridad de tipos en Tchar.h. Para ello, defina la constante `_NO_INLINING` en la línea de comandos. Este es el método más lento, pero garantiza prácticamente la seguridad de tipos.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directivas de preprocesador para asignaciones de texto genérico  
  
|# define|Versión compilada|Ejemplo|  
|---------------|----------------------|-------------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] (carácter ancho)|`_tcsrev` se asigna a `_wcsrev`|  
|`_MBCS`|Carácter multibyte|`_tcsrev` se asigna a `_mbsrev`|  
|Ninguno (la opción predeterminada no tiene definidos `_UNICODE` ni `_MBCS`)|SBCS ([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)])|`_tcsrev` se asigna a `strrev`|  
  
 Por ejemplo, la función de texto genérico `_tcsrev`, definida en Tchar.h, se asigna a `_mbsrev` si se ha definido `_MBCS` en el programa, o a `_wcsrev` si se ha definido `_UNICODE`. De lo contrario, `_tcsrev` se asigna a `strrev`. Las asignaciones de otros tipos de datos se proporcionan en Tchar.h para mayor comodidad en la programación, pero `_TCHAR` es la más útil.  
  
### <a name="generic-text-data-type-mappings"></a>Asignaciones de tipos de datos de texto genérico  
  
|Texto genérico <br /><br /> Nombre de tipo de datos|_UNICODE y<br /><br /> _MBCS no definidos|_MBCS<br /><br /> Definido|_UNICODE<br /><br /> Definido|  
|--------------------------------------|----------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`unsigned int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` o `_TEXT`|Sin efecto (quitado por el preprocesador)|Sin efecto (quitado por el preprocesador)|`L` (convierte el carácter o la cadena siguiente en su equivalente de [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)])|  
  
 Para obtener una lista de asignaciones de texto genérico de rutinas, variables y otros objetos, consulte [asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md) en la referencia de la biblioteca de tiempo de ejecución.  
  
> [!NOTE]
>  No utilice la familia `str` de funciones con cadenas de Unicode, ya que probablemente contendrán bytes nulos incrustados. Del mismo modo, no use la familia de funciones `wcs` con cadenas MBCS (o SBCS).  
  
 Los siguientes fragmentos de código muestran el uso de `_TCHAR` y `_tcsrev` para la asignación con los modelos MBCS, [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] y SBCS.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Si se ha definido `_MBCS`, el preprocesador asigna este fragmento a este código:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Si se ha definido `_UNICODE`, el preprocesador asigna este fragmento a este código:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Si no se han definido `_MBCS` ni `_UNICODE`, el preprocesador asigna el fragmento a código [!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)] de un solo byte, como se indica a continuación:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Por lo tanto, se puede crear, mantener y compilar un único archivo de código fuente para su ejecución con rutinas específicas de cualquiera de los tres tipos de juegos de caracteres.  
  
## <a name="see-also"></a>Vea también  
 [Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)   
 [Uso de tipos de datos de TCHAR.H con código _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)