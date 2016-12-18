---
title: "Advertencia de las herramientas del vinculador LNK4222 | Microsoft Docs"
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
  - "LNK4222"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4222"
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4222
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no debería asignarse un ordinal al símbolo 'símbolo' exportado  
  
 Los símbolos siguientes no deben exportarse mediante un ordinal:  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 Estas funciones siempre se localizan por su nombre, mediante `GetProcAddress`.  El vinculador advierte de este tipo de exportación, ya que puede dar como resultado una imagen de mayor tamaño.  Esto puede suceder si el intervalo de las exportaciones de ordinal es grande y contiene relativamente pocas exportaciones.  Por ejemplo,  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 requerirá 100 ranuras en la tabla de direcciones de exportación, siendo 98 \(2\-99\) puramente de relleno.  Por otro lado,  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 requerirá dos ranuras. \(No olvide que también puede exportar con la opción del vinculador [\/EXPORT](../../build/reference/export-exports-a-function.md).\)