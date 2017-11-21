---
title: Clase CHandle | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
dev_langs: C++
helpviewer_keywords: CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ed254b49c61f873e1d85fd0600c371c03ac246a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="chandle-class"></a>Clase CHandle
Esta clase proporciona métodos para crear y usar un identificador de objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CHandle
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHandle::CHandle](#chandle)|El constructor.|  
|[CHandle:: ~ CHandle](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHandle::Attach](#attach)|Llamar a este método para asociar la `CHandle` objeto en un identificador existente.|  
|[CHandle::Close](#close)|Llamar a este método para cerrar un `CHandle` objeto.|  
|[CHandle::Detach](#detach)|Llamar a este método para separar un identificador de un `CHandle` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHandle::operator identificador](#operator_handle)|Devuelve el valor del identificador almacenado.|  
|[CHandle::operator =](#operator_eq)|Operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|La variable de miembro que almacena el identificador.|  
  
## <a name="remarks"></a>Comentarios  
 A `CHandle` cada vez que se requiere un identificador de objeto que se puede usar: la principal diferencia es que la `CHandle` objeto se eliminan automáticamente.  
  
> [!NOTE]
>  Algunas funciones de la API utilizará NULL como un identificador vacío o no es válido, mientras que otros usan INVALID_HANDLE_VALUE. `CHandle`solo utiliza NULL y trata INVALID_HANDLE_VALUE como un identificador real. Si se llama a una API que puede devolver INVALID_HANDLE_VALUE, debe comprobar este valor antes de llamar a [CHandle::Attach](#attach) o pasarlo a la `CHandle` constructor y en su lugar, pase el valor NULL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="attach"></a>CHandle::Attach  
 Llamar a este método para asociar la `CHandle` objeto en un identificador existente.  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `h`  
 `CHandle`asumirá la propiedad del identificador `h`.  
  
### <a name="remarks"></a>Comentarios  
 Asigna la `CHandle` el objeto a la `h` controlar. En las compilaciones de depura, se generará una ATLASSERT si `h` es NULL. Se realiza ninguna otra comprobación en cuanto a la validez del identificador.  
  
##  <a name="chandle"></a>CHandle::CHandle  
 El constructor.  
  
```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `h`  
 Un identificador existente o `CHandle`.  
  
### <a name="remarks"></a>Comentarios  
 Crea un nuevo `CHandle` objeto, utilizando opcionalmente un identificador existente o `CHandle` objeto.  
  
##  <a name="dtor"></a>CHandle:: ~ CHandle  
 Destructor.  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera la `CHandle` objeto mediante una llamada a [CHandle::Close](#close).  
  
##  <a name="close"></a>CHandle::Close  
 Llamar a este método para cerrar un `CHandle` objeto.  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Cierra un identificador de objeto abierto. Si el identificador no es NULL, lo que será el caso si **cerrar** ya ha sido llama, se producirán un ATLASSERT en compilaciones de depuración.  
  
##  <a name="detach"></a>CHandle::Detach  
 Llamar a este método para separar un identificador de un `CHandle` objeto.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador que se va a separar.  
  
### <a name="remarks"></a>Comentarios  
 Libera la propiedad del identificador.  
  
##  <a name="m_h"></a>CHandle::m_h  
 La variable de miembro que almacena el identificador.  
  
```
HANDLE m_h;
```  
  
##  <a name="operator_eq"></a>CHandle::operator =  
 El operador de asignación.  
  
```
CHandle& operator=(CHandle& h) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `h`  
 `CHandle`asumirá la propiedad del identificador `h`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al nuevo `CHandle` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si el `CHandle` objeto actualmente contiene un identificador, se cerrará. El `CHandle` del objeto que se pasa en tendrá su referencia de identificador que se establece en NULL. Esto garantiza que dos `CHandle` objetos nunca contendrá el mismo identificador de activo.  
  
##  <a name="operator_handle"></a>CHandle::operator identificador  
 Devuelve el valor del identificador almacenado.  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve el valor almacenado en [CHandle::m_h](#m_h).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
