---
title: "Usar asignaciones de texto gen&#233;rico | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_UNICODE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_MBCS (tipo de datos)"
  - "_T (tipo)"
  - "_TCHAR (tipo)"
  - "_TEXT (tipo)"
  - "_TINT (tipo)"
  - "_TSCHAR (tipo)"
  - "_TUCHAR (tipo)"
  - "_TXCHAR (tipo)"
  - "_UNICODE (constante)"
  - "tipos de datos de texto genérico"
  - "asignaciones de texto genérico"
  - "asignaciones, texto genérico"
  - "MBCS (tipo de datos)"
  - "T (tipo)"
  - "TCHAR (tipo)"
  - "tipos de datos de TCHAR.H, asignaciones definidas en"
  - "TEXT (tipo)"
  - "TINT (tipo)"
  - "TSCHAR (tipo)"
  - "TUCHAR (tipo)"
  - "TXCHAR (tipo)"
  - "UNICODE (constante)"
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Usar asignaciones de texto gen&#233;rico
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Para simplificar el desarrollo de código para los diferentes mercados internacionales, la biblioteca en tiempo de ejecución de Microsoft proporciona las asignaciones Microsoft\- específicas de “genérico\- texto” para muchos tipos de datos, rutinas, y otros objetos.  Estas asignaciones se definen en TCHAR.H.  Puede utilizar estas asignaciones de nombre para escribir código genérico que se puede compilar para cualquiera de los tres tipos de juegos de caracteres: ASCII \(SBCS\), MBCS, o Unicode, dependiendo de la constante de manifiesto se define mediante una instrucción `#define` .  Las asignaciones de Genérico\- texto son extensiones de Microsoft que no son compatibles con ANSI.  
  
### Directivas de preprocesador para asignaciones de texto genérico  
  
|\#define|Versión compilada|Ejemplo|  
|--------------|-----------------------|-------------|  
|`_UNICODE`|Unicode \(carácter ancho\)|`_tcsrev` se asigna a `_wcsrev`|  
|`_MBCS`|Carácter multibyte|`_tcsrev` se asigna a `_mbsrev`|  
|Ninguno \(el valor predeterminado: ni `_UNICODE` ni `_MBCS` definido\)|SBCS \(ASCII\)|mapas de`_tcsrev` a `strrev`|  
  
 Por ejemplo, la función `_tcsrev`de genérico\- texto, definido en TCHAR.H, asigna a `mbsrev` si `MBCS` definida en el programa, o a `_wcsrev` si se ha definido `_UNICODE` .  Si no asigna de `_tcsrev` a `strrev`.  
  
 El tipo de datos `_TCHAR`de genérico\- texto, también definido en TCHAR.H, mapas para escribir `char` si se define `_MBCS` , escribir `wchar_t` si se define `_UNICODE` , y escribir `char` si se ha definido ninguna de las dos constantes.  Otras asignaciones de tipos de datos se proporcionan en TCHAR.H por comodidad de programación, pero `_TCHAR` es el tipo que es el más útil.  
  
### Asignaciones de tipos de datos de texto genérico  
  
|Nombre del tipo de datos de Genérico\- texto|SBCS \(\_UNICODE, \_MBCS no definidos\)|\_MBCS definido|\_UNICODE definido|  
|--------------------------------------------------|---------------------------------------------|---------------------|------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` o `_TEXT`|Sin efecto \(quitado por el preprocesador\)|Sin efecto \(quitado por el preprocesador\)|`L` \(convierte después de caracteres o de cadena a su equivalente de Unicode\)|  
  
 Para obtener una lista completa de las asignaciones de genérico\- texto de rutinas, variables, y otros objetos, vea [Asignaciones de Genérico\- texto](../c-runtime-library/generic-text-mappings.md).  
  
 Los fragmentos de código se muestra el uso de `_TCHAR` y de `_tcsrev` para asignar el MBCS, a Unicode, y a los modelos de SBCS.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Si se ha definido `MBCS` , el preprocesador asigna el fragmento anterior al código siguiente:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Si se ha definido `_UNICODE` , el preprocesador asigna el mismo fragmento al código siguiente:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Si no se han definido `_MBCS` ni `_UNICODE` , el preprocesador asigna el fragmento a código ASCII del solo\- byte, como sigue:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Así puede escribir, mantener, y compilar un único archivo de código fuente para ejecutarse con rutinas específicas de cualquiera de los tres tipos de juegos de caracteres.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md)   
 [Asignaciones de tipos de datos](../c-runtime-library/data-type-mappings.md)   
 [Asignaciones de constantes y de variables globales](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Asignaciones de rutinas](../c-runtime-library/routine-mappings.md)   
 [Ejemplo de programa de texto genérico](../c-runtime-library/a-sample-generic-text-program.md)