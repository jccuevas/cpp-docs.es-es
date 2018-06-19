---
title: 'Cómo: agregar el archivo DLL nativo a la caché Global de ensamblados | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7363de172eabc664bcde1e3bf42f8cc499e4251
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129543"
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