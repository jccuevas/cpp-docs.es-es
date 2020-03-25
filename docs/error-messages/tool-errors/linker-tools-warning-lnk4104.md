---
title: Advertencia de las herramientas del vinculador LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 604dccf01b3dffc0060546bebf19d64c16ebf965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193971"
---
# <a name="linker-tools-warning-lnk4104"></a>Advertencia de las herramientas del vinculador LNK4104

la exportación del símbolo ' Symbol ' debe ser privada

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

Esta advertencia se emite cuando se crea una biblioteca de importación para un archivo DLL y se exporta una de las funciones anteriores sin especificarla como privada en el archivo de definición de módulo. En general, estas funciones se exportan solo para su uso por parte de OLE. Colocarlos en la biblioteca de importación puede producir un comportamiento inusual cuando un programa vinculado a la biblioteca realiza llamadas a ellos de forma incorrecta. Para obtener más información sobre la palabra clave PRIVAte, vea [Exports](../../build/reference/exports.md).
