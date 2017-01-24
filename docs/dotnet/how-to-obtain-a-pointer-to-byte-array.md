---
title: "C&#243;mo: Obtener un puntero a una matriz de bytes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices de bytes"
  - "punteros, a una matriz de bytes"
ms.assetid: aea18073-3341-47f4-9f0e-04e03327037e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Obtener un puntero a una matriz de bytes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede obtener un puntero al bloque de una matriz <xref:System.Byte> tomando la dirección del primer elemento y asignándolo al puntero.  
  
## Ejemplo  
  
```  
// pointer_to_Byte_array.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Byte bArr[] = {1, 2, 3};  
   Byte* pbArr = &bArr[0];  
  
   array<Byte> ^ bArr2 = gcnew array<Byte>{1,2,3};  
   interior_ptr<Byte> pbArr2 = &bArr2[0];  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)