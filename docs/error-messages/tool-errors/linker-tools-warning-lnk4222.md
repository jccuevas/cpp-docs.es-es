---
title: Advertencia de las herramientas del vinculador LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: f74379861ad04142fd78a8e307af165072c9cadd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183038"
---
# <a name="linker-tools-warning-lnk4222"></a>Advertencia de las herramientas del vinculador LNK4222

el símbolo ' Symbol ' exportado no debe tener asignado un ordinal

Los siguientes símbolos no se deben exportar por ordinal:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Estas funciones siempre se encuentran por nombre, mediante `GetProcAddress`. El vinculador advierte de que este tipo de exportación es porque podría dar lugar a una imagen mayor. Esto podría ocurrir si el intervalo de las exportaciones ordinales es grande con relativamente pocas exportaciones. Por ejemplo,

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

requerirá 100 ranuras en la tabla de direcciones de exportación con 98 de ellas (2-99). Por otro lado

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

requerirá dos ranuras. (Tenga en cuenta que también puede exportar con la opción del enlazador [/Export](../../build/reference/export-exports-a-function.md) ).
