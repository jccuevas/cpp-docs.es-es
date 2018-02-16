---
title: 'Clase de valor Platform:: GUID | Documentos de Microsoft'
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
dev_langs:
- C++
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5323c934efb7d9416d1016f355390288885cb0c9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="platformguid-value-class"></a>Platform::Guid (Clase de valor)
Representa un tipo [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) en el sistema de tipos de Windows en tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public value struct Guid  
```  
  
### <a name="members"></a>Miembros  
 Guid tiene los métodos Equals(), GetHashCode() y ToString() que se derivan de [Platform::Object Class](../cppcx/platform-object-class.md), y el método GetTypeCode() que se deriva de [Platform::Type Class](../cppcx/platform-type-class.md). Guid también tiene los siguientes miembros.  
  
|Miembro|Descripción|  
|------------|-----------------|  
|[Guid](#ctor)|Inicializa una nueva instancia del struct Guid.|  
|[operator==](#operator-equality)|Operador Equals (de igualdad).|  
|[operator!=](#operator-not-equal)|Operador Not Equals (de desigualdad).|  
|[operator()](#operator-call)|Convierte un Guid en un GUID.|  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo sobre cómo generar un nuevo elemento Platform::Guid mediante el uso de la función de Windows [CoCreateGuid](http://msdn.microsoft.com/library/windows/desktop/ms688568\(v=vs.85\).aspx), consulte [WinRT component: How to generate a GUID?](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)(Componente de WinRT: ¿Cómo generar un GUID?).  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma  
  
 **Metadatos:** platform.winmd  

 
## <a name="ctor"></a> Constructores de GUID
Inicializa una nueva instancia de un struct Guid.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  );  
  
    Guid(GUID m);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n );  
```  
  
### <a name="parameters"></a>Parámetros  
 `a`  
 Los cuatro primeros bytes del identificador exclusivo global (GUID).  
  
 `b`  
 Los dos bytes siguientes del identificador exclusivo global (GUID).  
  
 `c`  
 Los dos bytes siguientes del identificador exclusivo global (GUID).  
  
 `d`  
 El byte siguiente del identificador exclusivo global (GUID).  
  
 `e`  
 El byte siguiente del identificador exclusivo global (GUID).  
  
 `f`  
 El byte siguiente del identificador exclusivo global (GUID).  
  
 `g`  
 El byte siguiente del identificador exclusivo global (GUID).  
  
 `h`  
 El byte siguiente del identificador exclusivo global (GUID).  
  
 `i`  
 El byte siguiente del identificador exclusivo global (GUID).  
  
 `j`  
 El byte siguiente del identificador exclusivo global (GUID).  
  
 `k`  
 El byte siguiente del identificador exclusivo global (GUID).  
  
 `m`  
 Un GUID, tal como se definió.  
  
 `n`  
 Los ocho bytes restantes del identificador exclusivo global (GUID).  
  

## <a name="operator-equality"></a> Guid::operator== Operator
Compara dos GUID.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
Platform::Guid::operator==  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es True si los dos GUID son iguales.

## <a name="operator-inequality"></a> Guid::operator!= Operator
Compara dos GUID.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
Platform::Guid::operator!=  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es True si los dos GUID no son iguales.



## <a name="operator-call"></a> ::Operator() (operador)
Convierte implícitamente un [estructura GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx)GUID a Platform:: GUID.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
Platform::Guid operator()  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un struct de Guid.  
  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)