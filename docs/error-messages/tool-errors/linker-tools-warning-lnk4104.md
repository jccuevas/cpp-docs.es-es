---
title: "Advertencia de las herramientas del vinculador LNK4104 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4104"
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la exportación del símbolo 'símbolo' debería ser PRIVATE  
  
 Este `symbol`puede ser cualquiera de los siguientes:  
  
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
  
 Se emite esta advertencia al compilar una biblioteca de importación para una DLL y exportar una de las funciones anteriores sin especificarla como PRIVATE en el archivo de definición de módulos.  En general, estas funciones se exportan para el uso exclusivo de OLE.  Colocarlas en la biblioteca de importación puede causar un comportamiento inesperado cuando un programa vinculado a la biblioteca realiza incorrectamente llamadas a las mismas.  Para obtener más información acerca de la palabra clave PRIVATE, vea [EXPORTS](../../build/reference/exports.md).