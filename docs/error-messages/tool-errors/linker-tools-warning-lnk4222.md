---
title: Las herramientas del vinculador LNK4222 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a54c452a5df6f99260d6d01fbf4bb9f2f17b955
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4222"></a>Advertencia de las herramientas del vinculador LNK4222
no debería asignarse un ordinal al símbolo exportado 'símbolo'  
  
 Los símbolos siguientes no se deberían exportar por ordinal:  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 Estas funciones siempre se localizan por su nombre, mediante `GetProcAddress`. El vinculador advierte de este tipo de exportación es porque pueden provocar en una imagen más grande. Esto podría suceder si el intervalo de las exportaciones de ordinal es grande con relativamente pocos exportaciones. Por ejemplo,  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 requerirá 100 ranuras disponibles en la tabla de direcciones de exportación con 98 de ellos (2-99) puramente de relleno. Por otro lado  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 requerirá dos ranuras. (Tenga en cuenta que también puede exportar con la [/exportación](../../build/reference/export-exports-a-function.md) opción del vinculador.)