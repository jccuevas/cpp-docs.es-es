---
title: Palabras clave de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 71e5c715c6065e8c05466bc3f09eba57606b304e
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="c-keywords"></a>Palabras clave de C
Las "palabras clave" son palabras que tienen un significado especial en C. En las fases de traducción 7 y 8, un identificador no puede escribirse igual, incluido el uso de mayúsculas y minúsculas, que palabra clave de C. (Vea una descripción de las [fases de traducción](../preprocessor/phases-of-translation.md) en la *Referencia del preprocesador*; para obtener información sobre los identificadores, vea [Identificadores](../c-language/c-identifiers.md)). El lenguaje C utiliza las siguientes palabras clave:  
  
|||||  
|-|-|-|-|  
|**auto**|**double**|**int**|**struct**|  
|**break**|**else**|**long**|**switch**|  
|**case**|**enum**|**register**|**typedef**|  
|**char**|**extern**|**return**|**union**|  
|**const**|**float**|**short**|**unsigned**|  
|**continue**|**for**|**signed**|**void**|  
|**default**|**goto**|**sizeof**|**volatile**|  
|**do**|**if**|**static**|**while**|  
  
 No puede volver a definir las palabras clave. En cambio, puede especificar el texto que se sustituirá para las palabras clave antes de la compilación mediante [directivas de preprocesador](../preprocessor/preprocessor-directives.md) de C.  
  
 **Específicos de Microsoft**  
  
 El estándar ANSI C permite reservar los identificadores con dos caracteres de subrayado iniciales para las implementaciones del compilador. Por consiguiente, la convención de Microsoft es que los nombres de palabras clave específicas de Microsoft vayan precedidos de subrayados dobles. Estas palabras no se pueden utilizar como nombres de identificador. Para obtener una descripción de las reglas ANSI para designar identificadores, incluido el uso de caracteres de subrayado dobles, vea [Identificadores](../c-language/c-identifiers.md).  
  
 El compilador de Microsoft C reconoce las palabras clave e identificadores especiales siguientes:  
  
|||||  
|-|-|-|-|  
|**__asm**|**dllimport**2|**__int8**|**naked**2|  
|**__based**1|**__except**|**__int16**|**__stdcall**|  
|**__cdecl**|**__fastcall**|**__int32**|**thread**2|  
|**__declspec**|**__finally**|**__int64**|**__try**|  
|**dllexport**2|**__inline**|**__leave**||  
  
 1. La palabra clave **__based** tiene usos limitados para las compilaciones de destino de 32 y 64 bits.  
  
 2. Estos son identificadores especiales cuando se usan con **__declspec**; su uso en otros contextos no está restringido.  
  
 Las extensiones de Microsoft están habilitadas de manera predeterminada. Para asegurarse de que los programas sean totalmente portables, puede deshabilitar las extensiones de Microsoft especificando la opción /Za (compilación para la compatibilidad con ANSI) durante la compilación. Al hacerlo, se deshabilitan las palabras clave específicas de Microsoft.  
  
 Con las extensiones de Microsoft habilitadas, puede usar las palabras clave antes indicadas en los programas. Para la compatibilidad con ANSI, la mayoría de estas palabras clave van precedidas de un subrayado doble. Las cuatro excepciones, **dllexport**, **dllimport**, **naked** y **thread**, solo se usan con **__declspec** y, por consiguiente, no requieren un subrayado doble inicial. Por compatibilidad con versiones anteriores, se admiten las versiones con un solo subrayado del resto de las palabras clave.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Elementos de C](../c-language/elements-of-c.md)
