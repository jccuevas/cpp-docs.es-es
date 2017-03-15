---
title: "Asignaciones de tipos de datos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_TXCHAR"
  - "_TUCHAR"
  - "_TINT"
  - "_TSCHAR"
  - "_TCHAR"
  - "TCHAR::H"
  - "TCHAR"
  - "_T"
  - "_TEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_T (tipo)"
  - "_TCHAR (tipo)"
  - "_TEXT (tipo)"
  - "_TINT (tipo)"
  - "_TSCHAR (tipo)"
  - "_TUCHAR (tipo)"
  - "_TXCHAR (tipo)"
  - "tipos de datos de texto genérico"
  - "T (tipo)"
  - "TCHAR (tipo)"
  - "tipos de datos de TCHAR.H, asignaciones definidas en"
  - "TEXT (tipo)"
  - "TINT (tipo)"
  - "TSCHAR (tipo)"
  - "TUCHAR (tipo)"
  - "TXCHAR (tipo)"
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Asignaciones de tipos de datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas asignaciones de tipo de datos se definen en TCHAR.H y dependen de si `_UNICODE` constante o `_MBCS` definida en el programa.  
  
 Para obtener información relacionada, vea [Utilizando tipos de datos de TCHAR.H con código de \_MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md).  
  
### Asignaciones de tipos de datos de texto genérico  
  
|Genérico\-texto<br /><br /> nombre del tipo de datos|SBCS \(\_UNICODE,<br /><br /> \_MBCS no<br /><br /> definido\)|\_MBCS<br /><br /> definición|\_UNICODE<br /><br /> definición|  
|--------------------------------------------------|----------------------------------------------------|---------------------------|------------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|  
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|  
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` o `_TEXT`|Sin efecto \(quitado por el preprocesador\)|Sin efecto \(quitado por el preprocesador\)|`L` \(convierte después de caracteres o de cadena a su equivalente de Unicode\)|  
  
## Vea también  
 [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md)   
 [Asignaciones de constantes y de variables globales](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Asignaciones de rutinas](../c-runtime-library/routine-mappings.md)   
 [Ejemplo de programa de texto genérico](../c-runtime-library/a-sample-generic-text-program.md)   
 [Usar asignaciones de texto genérico](../c-runtime-library/using-generic-text-mappings.md)