---
title: CStringData (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b872312352037e4cc0430c9b8dbb05df51ae7ac2
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881020"
---
# <a name="cstringdata-class"></a>CStringData (clase)
Esta clase representa los datos de un objeto de cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct CStringData
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddRef](#addref)|Incrementa el recuento de referencias del objeto de datos de cadena.|  
|[data](#data)|Recupera los datos de caracteres de un objeto de cadena.|  
|[IsLocked](#islocked)|Determina si el búfer del objeto string asociado está bloqueado.|  
|[IsShared](#isshared)|Determina si el búfer del objeto de cadena asociado se comparte.|  
|[Bloqueo](#lock)|Bloquea el búfer del objeto string asociado.|  
|[Release](#release)|Libera el objeto de cadena especificada.|  
|[Desbloquear](#unlock)|Desbloquea el búfer del objeto string asociado.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|Longitud de los datos asignados en `XCHAR`s (sin incluir el carácter nulo final)|  
|[nDataLength](#ndatalength)|Longitud de datos actualmente utilizados en `XCHAR`s (sin incluir el carácter nulo final)|  
|[nRefs](#nrefs)|El recuento de referencias actual del objeto.|  
|[pStringMgr](#pstringmgr)|Un puntero al administrador de cadena de este objeto de cadena.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase solo debería usarse por desarrolladores que implementan los administradores de la cadena personalizada. Para obtener más información sobre los administradores de la cadena personalizada, vea [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 Esta clase encapsula varios tipos de información y datos asociados con un objeto de cadena superior, como [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), o [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) objetos. Cada objeto de cadena superior contiene un puntero a su asociado `CStringData` objeto, lo que permite varios objetos de cadena para que apunte al mismo objeto de datos de cadena. Esta relación se representa mediante el recuento de referencias (`nRefs`) de la `CStringData` objeto.  
  
> [!NOTE]
>  En algunos casos, un tipo de cadena (como `CFixedString`) no compartirá un objeto de datos de cadena con más de un objeto de cadena mayor. Para obtener más información, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 Estos datos se componen de:  
  
-   El Administrador de memoria (de tipo [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) de la cadena.  
  
-   La longitud actual ( [nDataLength](#ndatalength)) de la cadena.  
  
-   La longitud asignada ( [nAllocLength](#nalloclength)) de la cadena. Por motivos de rendimiento, este puede ser diferente de la longitud de la cadena actual  
  
-   El recuento de referencias actual ( [nRefs](#nrefs)) de la `CStringData` objeto. Este valor se utiliza para determinar cuántos objetos de cadena comparten los mismos `CStringData` objeto.  
  
-   El búfer de caracteres reales ( [datos](#data)) de la cadena.  
  
    > [!NOTE]
    >  El búfer del carácter real del objeto de cadena asignado por el Administrador de cadenas y se anexa a la `CStringData` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpstr.h  
  
##  <a name="addref"></a>  CStringData::AddRef  
 Incrementa el recuento de referencias del objeto de cadena.  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Incrementa el recuento de referencias del objeto de cadena.  
  
> [!NOTE]
>  No llame a este método en una cadena con un recuento de referencias negativo, puesto que un número negativo indica que el búfer de cadena está bloqueado.  
  
##  <a name="data"></a>  CStringData::data  
 Devuelve un puntero al búfer de caracteres de un objeto de cadena.  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al búfer de caracteres del objeto de cadena.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para devolver el búfer de caracteres actual del objeto string asociado.  
  
> [!NOTE]
>  Este búfer no está asignada por el `CStringData` objeto pero por el Administrador de cadenas cuando sea necesario. Cuando asigna, el búfer se anexa al objeto de datos de cadena.  
  
##  <a name="islocked"></a>  CStringData::IsLocked  
 Determina si el búfer de caracteres está bloqueado.  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el búfer está bloqueado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para determinar si el búfer de caracteres de un objeto de cadena está bloqueado actualmente.  
  
##  <a name="isshared"></a>  CStringData::IsShared  
 Determina si se comparte el búfer de caracteres.  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el búfer es compartido; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para determinar si el búfer de caracteres de un objeto de datos de cadena actualmente se comparte entre varios objetos de cadena.  
  
##  <a name="lock"></a>  CStringData::Lock  
 Bloquea el búfer de caracteres del objeto string asociado.  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para bloquear el búfer de caracteres del objeto de datos de cadena. Bloqueo y desbloqueo se utilizan cuando el desarrollador requiere acceso directo al búfer de caracteres. Un buen ejemplo de bloqueo se demuestra el [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) métodos de `CSimpleStringT`.  
  
> [!NOTE]
>  Solo se puede bloquear un búfer de caracteres si el búfer no se comparte entre los objetos de cadena mayor.  
  
##  <a name="nalloclength"></a>  CStringData::nAllocLength  
 Longitud del búfer de caracteres asignados.  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>Comentarios  
 Almacena la longitud del búfer de datos asignado en `XCHAR`s (sin incluir el carácter nulo final).  
  
##  <a name="ndatalength"></a>  CStringData::nDataLength  
 Longitud actual del objeto de cadena.  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>Comentarios  
 Almacena la longitud de datos actualmente utilizados en `XCHAR`s (sin incluir el carácter nulo final).  
  
##  <a name="nrefs"></a>  CStringData::nRefs  
 Recuento de referencias del objeto de datos de cadena.  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>Comentarios  
 Almacena el recuento de referencias del objeto de datos de cadena. Este recuento indica el número de objetos de cadena superior que están asociados con el objeto de datos de cadena. Un valor negativo indica que el objeto de datos de cadena está bloqueado actualmente.  
  
##  <a name="pstringmgr"></a>  CStringData::pStringMgr  
 El Administrador de memoria del objeto string asociado.  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>Comentarios  
 Almacena el Administrador de memoria para el objeto de cadena asociado. Para obtener más información sobre los administradores de memoria y cadenas, vea [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="release"></a>  CStringData::Release  
 Disminuye el recuento de referencias del objeto de datos de cadena.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para reducir el recuento de referencias, liberando la `CStringData` estructura si el recuento de referencias llega a cero. Normalmente, esto se hace cuando se elimina un objeto de cadena y, por lo tanto, ya no necesita hacer referencia al objeto de datos de cadena.  
  
 Por ejemplo, el código siguiente llamaría `CStringData::Release` para el objeto de datos de cadena asociado con `str1`:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="unlock"></a>  CStringData::Unlock  
 Desbloquea el búfer de caracteres del objeto string asociado.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para desbloquear el búfer de caracteres del objeto de datos de cadena. Cuando se desbloquea un búfer, es que se puede compartir y pueden ser recuento de referencias.  
  
> [!NOTE]
>  Cada llamada a `Lock` debe coincidir con una llamada correspondiente a `Unlock`.  
  
 Bloqueo y desbloqueo se utilizan cuando el programador debe asegurarse de que no se comparta los datos de cadena. Un buen ejemplo de bloqueo se demuestra el [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) métodos de `CSimpleStringT`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases compartidas ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


