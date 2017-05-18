---
title: Clase CComGITPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
dev_langs:
- C++
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9fe9d9f6d03a6d72c1ce3332419c738570a53803
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomgitptr-class"></a>Clase CComGITPtr
Esta clase proporciona métodos para trabajar con punteros de interfaz y la tabla de interfaz global (GIT).  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class CComGITPtr
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de puntero de interfaz que se almacenará en la GIT.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|El constructor.|  
|[CComGITPtr:: ~ CComGITPtr](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|Llamar a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).|  
|[CComGITPtr::CopyTo](#copyto)|Llame a este método para copiar la interfaz de la tabla de interfaz global (GIT) al puntero pasado.|  
|[CComGITPtr::Detach](#detach)|Llamar a este método para desasociar la interfaz de la `CComGITPtr` objeto.|  
|[CComGITPtr::GetCookie](#getcookie)|Llamar a este método para devolver la cookie de la `CComGITPtr` objeto.|  
|[CComGITPtr::Revoke](#revoke)|Llamar a este método para quitar de la interfaz de la tabla de interfaz global (GIT).|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](#operator_dword)|Devuelve la cookie de la `CComGITPtr` objeto.|  
|[CComGITPtr::operator =](#operator_eq)|Operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|La cookie.|  
  
## <a name="remarks"></a>Comentarios  
 Los objetos que agregan el contador de referencias de subprocesamiento libre y necesitan utilizar punteros de interfaz obtenidos de otros objetos deben realizar pasos adicionales para asegurarse de que las interfaces se convierten correctamente. Normalmente, esto implica almacenar los punteros de interfaz en la GIT y obtener el puntero de la GIT cada vez que se utiliza. La clase `CComGITPtr` se proporciona para ayudarle a utilizar los punteros de interfaz almacenados en la GIT.  
  
> [!NOTE]
>  La función de la tabla de interfaz global sólo está disponible en Windows 95 con DCOM versión 1.1 y posterior, Windows 98, Windows NT 4.0 con Service Pack 3 y versiones posteriores y Windows 2000.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="attach"></a>CComGITPtr::Attach  
 Llamar a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).  
  
```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 El puntero de interfaz que se agregarán a la GIT.  
  
 `dwCookie`  
 Cookie que se utiliza para identificar el puntero de interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, se producirá un error de aserción si GIT no es válido o si la cookie es igual a NULL.  
  
##  <a name="ccomgitptr"></a>CComGITPtr::CComGITPtr  
 El constructor.  
  
```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `p`  
 Un puntero de interfaz que se almacenará en la tabla de interfaz global (GIT).  
  
 [in] `git`  
 Una referencia a un archivo `CComGITPtr` objeto.  
  
 [in] `dwCookie`  
 Cookie que se utiliza para identificar el puntero de interfaz.  
  
 [in] `rv`  
 El origen `CComGITPtr` mover datos de objeto.  
  
### <a name="remarks"></a>Comentarios  
 Crea un nuevo `CComGITPtr` objeto, utilizando opcionalmente existente `CComGITPtr` objeto.  
  
 El uso del constructor `rv` es un constructor de movimiento. Los datos se mueven desde el origen de `rv`y, a continuación, `rv` está desactivada.  
  
##  <a name="dtor"></a>CComGITPtr:: ~ CComGITPtr  
 Destructor.  
  
```
~CComGITPtr() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita la interfaz de la tabla de interfaz global (GIT), con [CComGITPtr::Revoke](#revoke).  
  
##  <a name="copyto"></a>CComGITPtr::CopyTo  
 Llame a este método para copiar la interfaz de la tabla de interfaz global (GIT) al puntero pasado.  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pp`  
 El puntero que va a recibir la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz de la GIT se copia en el puntero pasado. Debe liberar el puntero por el llamador cuando ya no sea necesario.  
  
##  <a name="detach"></a>CComGITPtr::Detach  
 Llamar a este método para desasociar la interfaz de la `CComGITPtr` objeto.  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cookie de la `CComGITPtr` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Depende del autor de la llamada para quitar de la interfaz de la GIT mediante [CComGITPtr::Revoke](#revoke).  
  
##  <a name="getcookie"></a>CComGITPtr::GetCookie  
 Llamar a este método para devolver la cookie de la `CComGITPtr` objeto.  
  
```
DWORD GetCookie() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cookie.  
  
### <a name="remarks"></a>Comentarios  
 La cookie es una variable que se utiliza para identificar una interfaz y su ubicación.  
  
##  <a name="m_dwcookie"></a>CComGITPtr::m_dwCookie  
 La cookie.  
  
```
DWORD m_dwCookie;
```  
  
### <a name="remarks"></a>Comentarios  
 La cookie es una variable de miembro que se utiliza para identificar una interfaz y su ubicación.  
  
##  <a name="operator_eq"></a>CComGITPtr::operator =  
 El operador de asignación.  
  
```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `p`  
 Un puntero a una interfaz.  
  
 [in] `git`  
 Referencia a un objeto `CComGITPtr`.  
  
 [in] `dwCookie`  
 Cookie que se utiliza para identificar el puntero de interfaz.  
  
 [in] `rv`  
 El `CComGITPtr` para mover datos desde.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CComGITPtr` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Asigna un nuevo valor a un `CComGITPtr` objeto desde un objeto existente o desde una referencia a una tabla de interfaz global.  
  
##  <a name="operator_dword"></a>CComGITPtr::operator DWORD  
 Devuelve la cookie asociada con la `CComGITPtr` objeto.  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La cookie es una variable que se utiliza para identificar una interfaz y su ubicación.  
  
##  <a name="revoke"></a>CComGITPtr::Revoke  
 Llame a este método para quitar de la interfaz actual de la tabla de interfaz global (GIT).  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Quita la interfaz de la GIT.  
  
## <a name="see-also"></a>Vea también  
 [Contador de referencias de subprocesamiento libre](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [Acceso a Interfaces entre apartamentos](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [Cuándo usar la tabla de interfaz Global](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Información general de la clase](../../atl/atl-class-overview.md)

