---
title: "Usar asignaciones de texto genérico | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _UNICODE
dev_langs:
- C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 17a3f4f7be76be9f23160e351466fee4f70b9272
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="using-generic-text-mappings"></a>Usar asignaciones de texto genérico
**Específicos de Microsoft**  
  
 Para simplificar el desarrollo de código para varios mercados internacionales, la biblioteca en tiempo de ejecución de Microsoft proporciona asignaciones de "texto genérico" específicas de Microsoft para muchos tipos de datos, rutinas y otros objetos. Estas asignaciones se definen en TCHAR.H. Puede usar estas asignaciones de nombres para escribir código genérico que se puede compilar para cualquiera de los tres tipos de juegos de caracteres: ASCII (SBCS), MBCS o Unicode, en función de una constante de manifiesto que se define mediante una instrucción `#define`. Las asignaciones de texto genérico son extensiones de Microsoft que no son compatibles con ANSI.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directivas de preprocesador para asignaciones de texto genérico  
  
|#define|Versión compilada|Ejemplo|  
|--------------|----------------------|-------------|  
|`_UNICODE`|Unicode (carácter ancho)|`_tcsrev` se asigna a `_wcsrev`|  
|`_MBCS`|Carácter multibyte|`_tcsrev` se asigna a `_mbsrev`|  
|Ninguno (la opción predeterminada no tiene definidos `_UNICODE` ni `_MBCS`)|SBCS (ASCII)|`_tcsrev` se asigna a `strrev`|  
  
 Por ejemplo, la función de texto genérico `_tcsrev`, definida en TCHAR.H, se asigna a `mbsrev` si se ha definido `MBCS` en el programa, o a `_wcsrev` si se ha definido `_UNICODE`. De lo contrario, `_tcsrev` se asigna a `strrev`.  
  
 El tipo de datos de texto genérico `_TCHAR`, también definido en TCHAR. H, se asigna al tipo `char` si se ha definido `_MBCS`, al tipo `wchar_t` si se ha definido `_UNICODE` y al tipo `char` si no se ha definido ninguna constante. Las asignaciones de otros tipos de datos se proporcionan en TCHAR.H para mayor comodidad en la programación, pero `_TCHAR` es el tipo más útil.  
  
### <a name="generic-text-data-type-mappings"></a>Asignaciones de tipos de datos de texto genérico  
  
|Nombre de tipo de datos de texto genérico|SBCS (_UNICODE, _MBCS no definidos)|_MBCS definido|_UNICODE definido|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` o `_TEXT`|Sin efecto (quitado por el preprocesador)|Sin efecto (quitado por el preprocesador)|`L` (convierte el carácter o la cadena siguiente en su equivalente de Unicode)|  
  
 Para obtener una lista completa de las asignaciones de texto genérico de rutinas, variables y otros objetos, vea [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md).  
  
 Los siguientes fragmentos de código muestran el uso de `_TCHAR` y `_tcsrev` para la asignación a los modelos MBCS, Unicode y SBCS.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Si se ha definido `MBCS`, el preprocesador asigna el fragmento anterior al siguiente código:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Si se ha definido `_UNICODE`, el preprocesador asigna el mismo fragmento al siguiente código:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Si no se han definido `_MBCS` ni `_UNICODE`, el preprocesador asigna el fragmento a código ASCII de byte único, como se indica a continuación:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Por lo tanto, se puede crear, mantener y compilar un único archivo de código fuente para su ejecución con rutinas específicas de cualquiera de los tres tipos de juegos de caracteres.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md)   
 [Asignaciones de tipos de datos](../c-runtime-library/data-type-mappings.md)   
 [Asignaciones de constantes y de variables globales](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Asignaciones de rutinas](../c-runtime-library/routine-mappings.md)   
 [Ejemplo de programa de texto genérico](../c-runtime-library/a-sample-generic-text-program.md)
