---
title: Las herramientas del vinculador LNK4104 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4104
dev_langs: C++
helpviewer_keywords: LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b26286f375f54a20e1d3db534576f692179ade24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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