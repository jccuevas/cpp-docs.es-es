---
title: "Error de las herramientas del vinculador LNK2031 | Microsoft Docs"
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
  - "LNK2031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2031"
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2031
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede generar p\/invoke para nombre\_representativo "declaración\_de\_función"; falta la convención de llamada en los metadatos  
  
 Cuando importe una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas son distintas en las compilaciones puras y nativas.  Para obtener más información acerca de las imágenes puras, vea [Código puro y comprobable](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## Ejemplo  
 Este ejemplo de código genera un componente con una función nativa exportada, cuya convención de llamada es implícitamente [\_\_cdecl](../../cpp/cdecl.md).  
  
```  
// LNK2031.cpp  
// compile with: /LD  
extern "C" {  
   __declspec(dllexport) int func() { return 3; }  
};  
```  
  
## Ejemplo  
 El ejemplo siguiente crea un cliente puro que utiliza la función nativa.  Sin embargo, la convención de llamada bajo **\/clr:pure** es [\_\_clrcall](../../cpp/clrcall.md).  El ejemplo siguiente genera el error LNK2031.  
  
```  
// LNK2031_b.cpp  
// compile with: /clr:pure LNK2031.lib  
// LNK2031 expected  
extern "C" int func();  
  
int main() {  
   return func();  
}  
```  
  
## Ejemplo  
 El siguiente ejemplo muestra cómo utilizar la función nativa de una imagen pura.  Tenga en cuenta el especificador de convención de llamada **\_\_cdecl** explícito.  
  
```  
// LNK2031_c.cpp  
// compile with: /clr:pure LNK2031.lib  
extern "C" int __cdecl func();  
  
int main() {  
   return func();  
}  
```