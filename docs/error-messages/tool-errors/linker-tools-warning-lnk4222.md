---
title: Las herramientas del vinculador LNK4222 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abc4f85fbc361b37d9325f9d395a1c34e1eeed2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106947"
---
# <a name="linker-tools-warning-lnk4222"></a>Advertencia de las herramientas del vinculador LNK4222

no debe asignarse un ordinal al símbolo exportado 'símbolo'

Los siguientes símbolos no se deben exportar por ordinal:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Estas funciones siempre se encuentran por su nombre, mediante `GetProcAddress`. El vinculador advierte acerca de este tipo de exportación es porque podría dar lugar a una imagen más grande. Esto podría suceder si el intervalo de las exportaciones de ordinal es grande con relativamente pocas exportaciones. Por ejemplo,

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

requerirá 100 ranuras en la tabla de direcciones de exportación con 98 de ellos (2-99) puramente de relleno. Por otro lado

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

requerirá dos ranuras. (Tenga en cuenta que también puede exportar con la [/EXPORT](../../build/reference/export-exports-a-function.md) opción del vinculador.)