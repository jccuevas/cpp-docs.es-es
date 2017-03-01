---
title: CSyncObject (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSyncObject
dev_langs:
- C++
helpviewer_keywords:
- CSyncObject class
- synchronization classes, CSyncObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a1f0c8ddfbfaf129bb18c14d36b998dd37d35899
ms.lasthandoff: 02/24/2017

---
# <a name="csyncobject-class"></a>CSyncObject (clase)
Una clase virtual pura que proporciona funcionalidad común para objetos de sincronización en Win32.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSyncObject : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSyncObject::CSyncObject](#csyncobject)|Construye un objeto `CSyncObject`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSyncObject::Lock](#lock)|Obtiene acceso al objeto de sincronización.|  
|[CSyncObject::Unlock](#unlock)|Obtiene acceso al objeto de sincronización.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDENTIFICADOR de CSyncObject::operator](#operator_handle)|Proporciona acceso al objeto de sincronización.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSyncObject::m_hObject](#m_hobject)|El identificador del objeto de sincronización subyacente.|  
  
## <a name="remarks"></a>Comentarios  
 La biblioteca Microsoft Foundation Class proporciona varias clases derivadas de `CSyncObject`. Estos son [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), y [CSemaphore](../../mfc/reference/csemaphore-class.md).  
  
 Para obtener información sobre cómo utilizar los objetos de sincronización, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="a-namecsyncobjecta--csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSyncObject::CSyncObject  
 Construye un objeto de sincronización con el nombre proporcionado.  
  
```  
explicit CSyncObject(LPCTSTR pstrName);  
virtual ~CSyncObject();
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrName`  
 El nombre del objeto. Si **NULL**, *pstrName* será null.  
  
##  <a name="a-namelocka--csyncobjectlock"></a><a name="lock"></a>CSyncObject::Lock  
 Llame a esta función para obtener acceso al recurso controlado por el objeto de sincronización.  
  
```  
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwTimeout`  
 Especifica la cantidad de tiempo en milisegundos de espera para que el objeto de sincronización esté disponible (señalado). Si **infinito**, `Lock` esperará hasta que el objeto está señalado antes de devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto de sincronización se señala, `Lock` devolverá correctamente y ahora, el subproceso propietario del objeto. Si el objeto de sincronización es no señalado (no disponible), `Lock` esperará a que el objeto de sincronización hasta que se señaliza hasta el número de milisegundos especificado en la *dwTimeOut* parámetro. Si el objeto de sincronización no señalará en la cantidad especificada de tiempo, `Lock` devuelve el error.  
  
##  <a name="a-namemhobjecta--csyncobjectmhobject"></a><a name="m_hobject"></a>CSyncObject::m_hObject  
 El identificador del objeto de sincronización subyacente.  
  
```  
HANDLE m_hObject;  
```  
  
##  <a name="a-nameoperatorhandlea--csyncobjectoperator-handle"></a><a name="operator_handle"></a>IDENTIFICADOR de CSyncObject::operator  
 Utilice este operador para obtener el identificador de la `CSyncObject` objeto.  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador del objeto de sincronización; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar el controlador para llamar directamente a las API de Windows.  
  
##  <a name="a-nameunlocka--csyncobjectunlock"></a><a name="unlock"></a>CSyncObject::Unlock  
 La declaración de `Unlock` sin parámetros es una función virtual pura y debe reemplazarse por todas las clases que derivan de `CSyncObject`.  
  
```  
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,  
    LPLONG lpPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lCount`  
 No se utiliza en la implementación predeterminada.  
  
 `lpPrevCount`  
 No se utiliza en la implementación predeterminada.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación predeterminada siempre devuelve **TRUE**.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de la declaración con dos parámetros siempre devuelve **TRUE**. Se llama a esta función para liberar el acceso al objeto de sincronización que pertenece al subproceso que realiza la llamada. La segunda declaración se proporciona para los objetos de sincronización como semáforos que permiten el más acceso de un recurso controlado.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




