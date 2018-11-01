---
title: Advertencia de las herramientas del vinculador LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 3d89b27c32b33b917abb7fc140eebf5924142423
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668133"
---
# <a name="linker-tools-warning-lnk4104"></a>Advertencia de las herramientas del vinculador LNK4104

la exportación del símbolo 'symbol' debería ser PRIVATE

El `symbol` puede ser uno de los siguientes:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

Esta advertencia se genera cuando se va a compilar una biblioteca de importación para un archivo DLL y exportar una de las funciones anteriores sin especificar como privada en el archivo de definición de módulo. En general, estas funciones se exportan para su uso sólo por OLE. Y los coloca en la biblioteca de importación pueden provocar un comportamiento poco habitual cuando un programa vinculado a la biblioteca incorrectamente realiza llamadas a ellos. Para obtener más información sobre la palabra clave privada, consulte [exportaciones](../../build/reference/exports.md).