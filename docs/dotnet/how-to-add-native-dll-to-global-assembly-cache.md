---
title: Procedimiento Agregar un archivo DLL nativo a la caché Global de ensamblados
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: b4b886dfef3185c1b3084ed02abcef1ad2630c11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222803"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Procedimiento Agregar un archivo DLL nativo a la caché Global de ensamblados

Puede colocar un archivo DLL nativo (no COM) en la caché Global de ensamblados.

## <a name="example"></a>Ejemplo

**/ASSEMBLYLINKRESOURCE** le permite incrustar un archivo DLL nativo en un ensamblado.

Para obtener más información, consulte [/ASSEMBLYLINKRESOURCE (vincular a recursos de .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
