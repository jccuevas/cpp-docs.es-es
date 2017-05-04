---
title: "IntPtr::op_explicit (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IntPtr::op_explicit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IntPtr::op_explicit (Método)"
ms.assetid: cc52e9d5-fe73-471b-8cff-d9f684ba6e20
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# IntPtr::op_explicit (Operador)
Convierte el parámetro especificado un IntPtr o un puntero a un valor de IntPtr.  
  
## Sintaxis  
  
```cpp  
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );  
```  
  
#### Parámetros  
 value1  
 Un puntero a un identificador o IntPtr.  
  
 value2  
 Un entero de 32 bits que se puede convertir en un objeto IntPtr.  
  
 value3  
 Un objeto IntPtr.  
  
## Valor devuelto  
 Los operadores primero y segundo devuelven un objeto IntPtr. El tercer operador devuelve un puntero al valor representado por el objeto IntPtr actual.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Platform::IntPtr \(Clase de valor\)](../cppcx/platform-intptr-value-class.md)