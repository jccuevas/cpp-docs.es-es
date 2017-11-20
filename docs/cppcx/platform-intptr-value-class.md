---
title: 'Clase de valor Platform:: IntPtr | Documentos de Microsoft'
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
dev_langs: C++
helpviewer_keywords: Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 4bd0fcdf8f7b7f825a087a2176babeb59bac4f05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="platformintptr-value-class"></a>Platform::IntPtr (Clase de valor)
Representa un puntero o un identificador con signo cuyo tamaño es específico de la plataforma (32 bits o 64 bits).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public value struct IntPtr  
```  
  
### <a name="members"></a>Miembros  
 IntPtr tiene los siguientes miembros:  
  
|Miembro|Descripción|  
|------------|-----------------|  
|[IntPtr](#ctor)|Inicializa una nueva instancia de IntPtr.|  
|[IntPtr::op_explicit (Operador)](#op-explicit)|Convierte el parámetro especificado un IntPtr o un puntero a un valor de IntPtr.|  
|[IntPtr:: Toint32](#toint32)|Convierte el IntPtr actual en un entero de 32 bits.|  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  

## <a name="ctor"> </a> IntPtr::IntPtr (Constructor)
Inicializa una nueva instancia de un objeto IntPtr con el valor especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );  
```  
  
### <a name="parameters"></a>Parámetros  
 valor  
 Un identificador o un puntero de 64 bits, o un puntero a un valor de 64 bits, o un valor de 32 bits que se puede convertir en un valor de 64 bits.  
  


## <a name="op-explicit"> </a> IntPtr::op_explicit (Operador)
Convierte el parámetro especificado un IntPtr o un puntero a un valor de IntPtr.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );  
```  
  
### <a name="parameters"></a>Parámetros  
 value1  
 Un puntero a un identificador o IntPtr.  
  
 value2  
 Un entero de 32 bits que se puede convertir en un objeto IntPtr.  
  
 value3  
 Un objeto IntPtr.  
  
### <a name="return-value"></a>Valor devuelto  
 Los operadores primero y segundo devuelven un objeto IntPtr. El tercer operador devuelve un puntero al valor representado por el objeto IntPtr actual.  
  


## <a name="toint32"></a> IntPtr:: Toint32 (método)
Convierte el valor IntPtr actual en un entero de 32 bits.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
int32 IntPtr::ToInt32();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero de 32 bits.  
  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)