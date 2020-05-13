---
title: Palabras clave de C
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: e1364e0edacd94efa4ade6c6892a57d619635a39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326799"
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
|**__asm**<sup>3</sup>|**dllimport**<sup>2</sup>|**__int8**<sup>3</sup>|**naked**<sup>2</sup>|
|**__based**<sup>1, 3</sup>|**__except**<sup>3</sup>|**__int16**<sup>3</sup>|**__stdcall**<sup>3</sup>|
|**__cdecl**<sup>3</sup>|**__fastcall**|**__int32**<sup>3</sup>|**thread**<sup>2</sup>|
|**__declspec**<sup>3</sup>|**__finally**<sup>3</sup>|**__int64**<sup>3</sup>|**__try**<sup>3</sup>|
|**dllexport**<sup>2</sup>|**__inline**<sup>3</sup>|**__leave**<sup>3</sup>||

<sup>1</sup> La palabra clave **__based** tiene usos limitados para las compilaciones de destino de 32 y 64 bits.

<sup>2</sup> Estos son identificadores especiales cuando se usan con **__declspec**; su uso en otros contextos no está restringido.

<sup>3</sup> Para compatibilidad con versiones anteriores, estas palabras clave están disponibles con dos caracteres de subrayado iniciales y un único carácter de subrayado inicial cuando se habilitan las extensiones de Microsoft.

Las extensiones de Microsoft están habilitadas de manera predeterminada. Para asegurarse de que los programas sean totalmente portables, puede deshabilitar las extensiones de Microsoft especificando la opción [/Za \(Deshabilitar las extensiones del lenguaje)](../build/reference/za-ze-disable-language-extensions.md) durante la compilación. Al hacerlo, se deshabilitan algunas las palabras clave específicas de Microsoft.

Con las extensiones de Microsoft habilitadas, puede usar las palabras clave antes indicadas en los programas. Para la compatibilidad con ANSI, la mayoría de estas palabras clave van precedidas de un subrayado doble. Las cuatro excepciones, **dllexport**, **dllimport**, **naked** y **thread**, solo se usan con **__declspec** y, por consiguiente, no requieren un subrayado doble inicial. Por compatibilidad con versiones anteriores, se admiten las versiones con un solo subrayado del resto de las palabras clave.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Elementos de C](../c-language/elements-of-c.md)
