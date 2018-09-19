---
title: Las herramientas del vinculador LNK4104 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4104
dev_langs:
- C++
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6304f3ea928c89f4756a4594270ebb7914324f85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057267"
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