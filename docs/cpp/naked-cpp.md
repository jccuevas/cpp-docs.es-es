---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: cfe3631086515e4e31c7d4188d46e3a7440662b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177955"
---
# <a name="naked-c"></a>naked (C++)

**Específicos de Microsoft**

En el caso de las funciones declaradas con el atributo **naked** , el compilador genera código sin código de prólogo y epílogo. Puede utilizar esta característica para escribir sus propias secuencias de código de prólogo/epílogo mediante código del ensamblador alineado. Las funciones naked son especialmente útiles al escribir controladores de dispositivos virtuales.  Tenga en cuenta que el atributo **naked** solo es válido en x86 y ARM, y no está disponible en x64.

## <a name="syntax"></a>Sintaxis

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Observaciones

Dado que el atributo **naked** solo es pertinente para la definición de una función y no es un modificador de tipo, las funciones Naked deben usar la sintaxis de atributo extendido y la palabra clave [__declspec](../cpp/declspec.md) .

El compilador no puede generar una función insertada para una función marcada con el atributo Naked, aunque la función también esté marcada con la palabra clave [__forceinline](inline-functions-cpp.md) .

El compilador emite un error si el atributo **naked** se aplica a un valor distinto de la definición de un método no miembro.

## <a name="examples"></a>Ejemplos

Este código define una función con el atributo **naked** :

```
__declspec( naked ) int func( formal_parameters ) {}
```

O bien, como alternativa:

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

El atributo **naked** solo afecta a la naturaleza de la generación de código del compilador para las secuencias de prólogo y epílogo de la función. No afecta al código que se genera para llamar a esas funciones. Por lo tanto, el atributo **naked** no se considera parte del tipo de la función y los punteros de función no pueden tener el atributo **naked** . Además, el atributo **naked** no se puede aplicar a una definición de datos. Por ejemplo, en este ejemplo de código se genera un error:

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

El atributo **naked** solo es pertinente para la definición de la función y no se puede especificar en el prototipo de la función. Por ejemplo, esta declaración genera un error del compilador:

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Llamadas de función naked](../cpp/naked-function-calls.md)
