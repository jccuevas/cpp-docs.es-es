---
title: Clase CHandle | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CHandle
- ATL::CHandle
- CHandle
dev_langs:
- C++
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: bbc0703ae5eaab01c0819be7e378509c7dc579ef
ms.lasthandoff: 02/24/2017

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
|[IDENTIFICADOR de CHandle::operator](#operator_handle)|Devuelve el valor del identificador almacenado.|  
|[CHandle::operator =](#operator_eq)|Operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|La variable miembro que almacena el identificador.|  
  
## <a name="remarks"></a>Comentarios  
 Un `CHandle` cada vez que se requiere un identificador de objeto que se puede usar: la diferencia principal es que la `CHandle` objeto se eliminan automáticamente.  
  
> [!NOTE]
>  Algunas funciones de API utilizarán NULL como un identificador vacío o no válido, mientras que otros usan INVALID_HANDLE_VALUE. `CHandle`solo utiliza NULL y trate INVALID_HANDLE_VALUE como un identificador real. Si se llama a una API que puede devolver INVALID_HANDLE_VALUE, debe comprobar este valor antes de llamar a [CHandle::Attach](#attach) o pasarlo a la `CHandle` constructor y en su lugar, pase NULL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="a-nameattacha--chandleattach"></a><a name="attach"></a>CHandle::Attach  
 Llamar a este método para asociar la `CHandle` objeto en un identificador existente.  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `h`  
 `CHandle`asumirá la propiedad del identificador `h`.  
  
### <a name="remarks"></a>Comentarios  
 Asigna la `CHandle` de objeto para el `h` controlar. En las compilaciones depura, se generará una ATLASSERT si `h` es NULL. Se realiza ninguna otra comprobación en cuanto a la validez del identificador.  
  
##  <a name="a-namechandlea--chandlechandle"></a><a name="chandle"></a>CHandle::CHandle  
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
  
##  <a name="a-namedtora--chandlechandle"></a><a name="dtor"></a>CHandle:: ~ CHandle  
 Destructor.  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera el `CHandle` objeto mediante una llamada a [CHandle::Close](#close).  
  
##  <a name="a-nameclosea--chandleclose"></a><a name="close"></a>CHandle::Close  
 Llamar a este método para cerrar un `CHandle` objeto.  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Cierra un identificador de objeto abierto. Si el identificador es NULL, que será el caso si **cerrar** ya ha sido llamado, se generará una ATLASSERT en compilaciones de depuración.  
  
##  <a name="a-namedetacha--chandledetach"></a><a name="detach"></a>CHandle::Detach  
 Llamar a este método para separar un identificador de un `CHandle` objeto.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador que se va a separar.  
  
### <a name="remarks"></a>Comentarios  
 Libera la propiedad del identificador.  
  
##  <a name="a-namemha--chandlemh"></a><a name="m_h"></a>CHandle::m_h  
 La variable miembro que almacena el identificador.  
  
```
HANDLE m_h;
```  
  
##  <a name="a-nameoperatoreqa--chandleoperator-"></a><a name="operator_eq"></a>CHandle::operator =  
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
 Si el `CHandle` objeto actualmente contiene un identificador, se cerrará. El `CHandle` del objeto que se pasa en tendrá su referencia de identificador establecido en NULL. Esto garantiza que dos `CHandle` objetos nunca contendrán el mismo identificador de activo.  
  
##  <a name="a-nameoperatorhandlea--chandleoperator-handle"></a><a name="operator_handle"></a>IDENTIFICADOR de CHandle::operator  
 Devuelve el valor del identificador almacenado.  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve el valor almacenado en [CHandle::m_h](#m_h).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

