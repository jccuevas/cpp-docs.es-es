---
title: Atributos extendidos de clase de almacenamiento de C
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: c2e372ebe93b9240ac6f489e8b1aefc1fbbded80
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857156"
---
# <a name="c-extended-storage-class-attributes"></a>Atributos extendidos de clase de almacenamiento de C

**Específicos de Microsoft**

Encontrará información más actualizada sobre este tema en [__declspec (Referencia de C++)](../cpp/declspec.md).

La sintaxis de atributo extendido simplifica y normaliza las extensiones específicas de Microsoft para el lenguaje C. Los atributos de clase de almacenamiento que usan la sintaxis de atributo extendido son thread, naked, dllimport y dllexport.

La sintaxis de atributo extendido para especificar información de clase de almacenamiento utiliza la palabra clave __declspec, que especifica que una instancia de un tipo determinado se debe almacenar con un atributo de clase de almacenamiento específico de Microsoft (thread, naked, dllimport o dllexport). Algunos ejemplos de otros modificadores de clase de almacenamiento son las palabras clave static y extern. Sin embargo, estas palabras clave forman parte del estándar ANSI C y, como tales, no se tratan con la sintaxis de atributo extendido.

## <a name="syntax"></a>Sintaxis

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *extended-decl-modifier-seq* **)**  /\* Específico de Microsoft \*/

*extended-decl-modifier-seq*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Específico de Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*extended-decl-modifier*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Específico de Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

El espacio en blanco separa los modificadores de la declaración. Observe que el elemento *extended-decl-modifier-seq* puede estar vacío; en este caso, __declspec no tiene ningún efecto.

Los atributos de clase de almacenamiento thread, naked, dllimport y dllexport son una propiedad solo de la declaración de los datos o función a los que se aplican; no vuelven a definir los atributos de tipo de la propia función. El atributo thread afecta solo a los datos. El atributo naked solo afecta a las funciones. Los atributos dllimport y dllexport afectan a funciones y datos.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Declaraciones y tipos](../c-language/declarations-and-types.md)
