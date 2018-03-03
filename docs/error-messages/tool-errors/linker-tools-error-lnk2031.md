---
title: Las herramientas del vinculador LNK2031 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2031
dev_langs:
- C++
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a519b4241c9ffabaeeb387cc8e4997125d57781
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2031"></a>Error de las herramientas del vinculador LNK2031
no se puede generar p/invoke para "declaración_de_función"; convención de llamada que faltan en los metadatos  
  
 Al intentar importar una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas son diferentes entre compilaciones nativas y puras. Para obtener más información acerca de las imágenes puras, vea [código puro y comprobable (C++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo de código genera un componente con una función exportada y nativa, cuya convención de llamada es implícitamente [__cdecl](../../cpp/cdecl.md).  
  
```  
// LNK2031.cpp  
// compile with: /LD  
extern "C" {  
   __declspec(dllexport) int func() { return 3; }  
};  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente crea a un cliente puro que usa la función nativa. Sin embargo, la convención de llamada en **/CLR: pure** es [__clrcall](../../cpp/clrcall.md). El ejemplo siguiente genera el error LNK2031.  
  
```  
// LNK2031_b.cpp  
// compile with: /clr:pure LNK2031.lib  
// LNK2031 expected  
extern "C" int func();  
  
int main() {  
   return func();  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo utilizar la función nativa de una imagen pura. Tenga en cuenta la explícita **__cdecl** especificador de convención de llamada.  
  
```  
// LNK2031_c.cpp  
// compile with: /clr:pure LNK2031.lib  
extern "C" int __cdecl func();  
  
int main() {  
   return func();  
}  
```