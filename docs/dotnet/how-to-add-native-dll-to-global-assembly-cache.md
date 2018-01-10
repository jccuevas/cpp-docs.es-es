---
title: "Cómo: agregar el archivo DLL nativo a la caché Global de ensamblados | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: be55fd47cd6024d0660ed0c3e4594c9430f80cc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Cómo: Agregar un archivo DLL nativo a la memoria caché global de ensamblados
Se puede colocar un archivo DLL nativo (no COM) en la caché Global de ensamblados.  
  
## <a name="example"></a>Ejemplo  
 **/ASSEMBLYLINKRESOURCE** le permite incrustar un archivo DLL nativo en un ensamblado.  
  
 Para obtener más información, consulte [/ASSEMBLYLINKRESOURCE (vincular a recursos de .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## <a name="see-also"></a>Vea también  
 [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)