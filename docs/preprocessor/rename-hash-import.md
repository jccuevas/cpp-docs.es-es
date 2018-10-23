---
title: cambiar el nombre (#import) | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b8525a321f56ab5e9bfe2f8e8cee7be9cd26788
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808191"
---
# <a name="rename-import"></a>cambiar el nombre (\#importar)

**Específicos de C++**

Resuelve problemas del conflicto de nombres.

## <a name="syntax"></a>Sintaxis

```
rename("OldName","NewName")
```

### <a name="parameters"></a>Parámetros

*OldName*<br/>
Nombre anterior en la biblioteca de tipos.

*NewName*<br/>
Nombre usado en lugar del nombre anterior.

## <a name="remarks"></a>Comentarios

Si se especifica este atributo, el compilador reemplaza todas las apariciones de *OldName* en una biblioteca de tipos con el proporcionado por el usuario *NewName* en los archivos de encabezado resultante.

Este atributo se puede utilizar cuando un nombre en la biblioteca de tipos coincide con una definición de macro en los archivos de encabezado del sistema. Si no se puede resolver esta situación, se generarán distintos errores de sintaxis, como [Error del compilador C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) y [Error del compilador C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> La sustitución se aplica a un nombre usado en la biblioteca de tipos, no a un nombre usado en el archivo de encabezado resultante.

Suponga, por ejemplo, que hay una propiedad denominada `MyParent` en una biblioteca de tipos y que se define una macro `GetMyParent` en un archivo de encabezado y se utiliza antes de `#import`. Puesto que `GetMyParent` es el nombre predeterminado de una función de contenedor para el control de errores `get` propiedad, se producirá un conflicto de nombres. Para solucionar el problema, utilice el siguiente atributo en la instrucción `#import`:

```cpp
rename("MyParent","MyParentX")
```

que cambia el nombre `MyParent` en la biblioteca de tipos. Un intento de cambiar el nombre del contenedor `GetMyParent` producirá un error:

```cpp
rename("GetMyParent","GetMyParentX")
```

Esto se debe a que el nombre `GetMyParent` solo aparece en el archivo de encabezado resultante de la biblioteca de tipos.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)