---
title: Advertencia de las herramientas del vinculador LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: 52a4fee532eb9997dcf013f95246b27fdffc4c20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563103"
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