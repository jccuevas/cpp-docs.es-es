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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c001d0d1ca8e756b24d97051d100e7d71723569c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 El tipo del puntero de interfaz que se almacenará en la GIT.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|El constructor.|  
|[CComGITPtr:: ~ CComGITPtr](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|Llamar a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).|  
|[CComGITPtr::CopyTo](#copyto)|Llamar a este método para copiar la interfaz de la tabla de interfaz global (GIT) en el puntero ha pasado.|  
|[CComGITPtr::Detach](#detach)|Llamar a este método para desasociar la interfaz de la `CComGITPtr` objeto.|  
|[CComGITPtr::GetCookie](#getcookie)|Llamar a este método para devolver la cookie de la `CComGITPtr` objeto.|  
|[CComGITPtr::Revoke](#revoke)|Llame a este método para quitar la interfaz de la tabla de interfaz global (GIT).|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](#operator_dword)|Devuelve la cookie de la `CComGITPtr` objeto.|  
|[CComGITPtr::operator =](#operator_eq)|Operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|La cookie.|  
  
## <a name="remarks"></a>Comentarios  
 Objetos que agregan el contador de referencias de subprocesamiento libre y necesitan usar punteros de interfaz obtenidos de otros objetos deben realizar pasos adicionales para asegurarse de que las interfaces se serializan correctamente. Normalmente, esto implica almacenar los punteros de interfaz en la GIT y obtener el puntero de la GIT cada vez que se utilice. La clase `CComGITPtr` se proporciona para ayudarle a utilizar los punteros de interfaz almacenados en la GIT.  
  
> [!NOTE]
>  La funcionalidad de la tabla de interfaz global solo está disponible en Windows 95 con DCOM versión 1.1 y versiones posteriores, Windows 98, Windows NT 4.0 con Service Pack 3 y versiones posteriores y Windows 2000.  
  
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
 Puntero de interfaz que se va a agregar a la GIT.  
  
 `dwCookie`  
 La cookie usada para identificar el puntero de interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se producirá un error de aserción si la GIT no es válida, o si la cookie es igual a NULL.  
  
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
 Cookie que se usa para identificar el puntero de interfaz.  
  
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
 Llamar a este método para copiar la interfaz de la tabla de interfaz global (GIT) en el puntero ha pasado.  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pp`  
 El puntero que se va a recibir la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz de la GIT se copia en el puntero ha pasado. El puntero debe liberarla el llamador cuando ya no sea necesario.  
  
##  <a name="detach"></a>CComGITPtr::Detach  
 Llamar a este método para desasociar la interfaz de la `CComGITPtr` objeto.  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cookie de la `CComGITPtr` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Depende del autor de la llamada para quitar la interfaz de GIT, con [CComGITPtr::Revoke](#revoke).  
  
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
 La cookie es una variable de miembro que se usa para identificar una interfaz y su ubicación.  
  
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
 Cookie que se usa para identificar el puntero de interfaz.  
  
 [in] `rv`  
 El `CComGITPtr` para mover datos desde.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la actualización `CComGITPtr` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Asigna un nuevo valor a un `CComGITPtr` objeto, ya sea desde un objeto existente o de una referencia a una tabla de interfaz global.  
  
##  <a name="operator_dword"></a>CComGITPtr::operator DWORD  
 Devuelve la cookie asociada con la `CComGITPtr` objeto.  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La cookie es una variable que se utiliza para identificar una interfaz y su ubicación.  
  
##  <a name="revoke"></a>CComGITPtr::Revoke  
 Llamar a este método para quitar la interfaz actual de la tabla de interfaz global (GIT).  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Quita la interfaz de la GIT.  
  
## <a name="see-also"></a>Vea también  
 [Contador de referencias de subprocesamiento libre](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [Acceso a Interfaces a través de apartamentos](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [Cuándo se debe utilizar la tabla de interfaz Global](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Información general de clases](../../atl/atl-class-overview.md)
