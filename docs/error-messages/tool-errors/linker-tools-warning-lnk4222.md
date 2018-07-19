---
title: Las herramientas del vinculador LNK4222 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359af4c4d3b1079b2d56f108bff0ee1488ea71f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302154"
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