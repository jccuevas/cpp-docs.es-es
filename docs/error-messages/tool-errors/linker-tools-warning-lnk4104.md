---
title: Las herramientas del vinculador LNK4104 advertencia | Documentos de Microsoft
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
ms.openlocfilehash: d9ea3e074cc0db9591cd0ffe9329ff7f1936563f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4104"></a>Advertencia de las herramientas del vinculador LNK4104
la exportación del símbolo 'symbol' debe ser privada  
  
 La `symbol` puede ser uno de los siguientes:  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllGetDocumentation`  
  
-   `DllInitialize`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllRegisterServerExW`  
  
-   `DllUnload`  
  
-   `DllUnregisterServer`  
  
-   `RasCustomDeleteEntryNotify`  
  
-   `RasCustomDial`  
  
-   `RasCustomDialDlg`  
  
-   `RasCustomEntryDlg`  
  
 Esta advertencia se emite cuando se está generando una biblioteca de importación para un archivo DLL y exportar una de las funciones anteriores sin especificarla como PRIVATE en el archivo de definición de módulo. En general, estas funciones se exportan para su uso exclusivo de OLE. Colocarlas en la biblioteca de importación pueden provocar un comportamiento poco habitual cuando un programa vinculado a la biblioteca incorrectamente realiza llamadas a ellos. Para obtener más información acerca de la palabra clave privada, consulte [exportaciones](../../build/reference/exports.md).