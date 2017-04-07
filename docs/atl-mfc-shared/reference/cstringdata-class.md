---
title: Clase CStringData | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 16
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b7dfebebbec7acc774fa2e63ab9fafed788f679a
ms.lasthandoff: 02/24/2017

---
# <a name="cstringdata-class"></a>Clase CStringData
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
|[IsLocked](#islocked)|Determina si el búfer del objeto de cadena asociado está bloqueado.|  
|[IsShared](#isshared)|Determina si el búfer del objeto de cadena asociado se comparte.|  
|[Bloqueo](#lock)|Bloquea el búfer del objeto de cadena asociado.|  
|[Release](#release)|Libera el objeto de cadena especificada.|  
|[Desbloquear](#unlock)|Desbloquea el búfer del objeto de cadena asociado.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|Longitud de datos asignados `XCHAR`s (sin incluir el carácter nulo final)|  
|[nDataLength](#ndatalength)|Longitud de datos actualmente utilizados en `XCHAR`s (sin incluir el carácter nulo final)|  
|[nRefs](#nrefs)|El recuento de referencias actual del objeto.|  
|[pStringMgr](#pstringmgr)|Un puntero al administrador de cadena de este objeto de cadena.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase solo debe usarse por desarrolladores que implementan administradores de la cadena personalizada. Para obtener más información sobre los administradores de la cadena personalizada, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 Esta clase encapsula varios tipos de información y los datos asociados con un objeto de cadena superior, como [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), o [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) objetos. Cada objeto de cadena superior contiene un puntero a su asociado `CStringData` objeto, que permite a varios objetos de cadena para que apunte al mismo objeto de datos de cadena. Esta relación se representa mediante el recuento de referencias ( `nRefs`) de la `CStringData` objeto.  
  
> [!NOTE]
>  En algunos casos, un tipo de cadena (como **CFixedString**) no compartirá un objeto de datos de cadena con más de un objeto de cadena mayor. Para obtener más información, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 Estos datos se componen de:  
  
-   El Administrador de memoria (de tipo [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) de la cadena.  
  
-   La longitud actual ( [nDataLength](#ndatalength)) de la cadena.  
  
-   La longitud de la asignación ( [nAllocLength](#nalloclength)) de la cadena. Por motivos de rendimiento, puede ser distinta de la longitud de la cadena actual  
  
-   El recuento de referencias actual ( [nRefs](#nrefs)) de la `CStringData` objeto. Este valor se utiliza para determinar cuántos objetos string comparten el mismo `CStringData` objeto.  
  
-   El búfer de caracteres reales ( [datos](#data)) de la cadena.  
  
    > [!NOTE]
    >  El búfer de carácter real del objeto de cadena asignado por el Administrador de cadenas y se anexa a la `CStringData` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpstr.h  
  
##  <a name="addref"></a>CStringData::AddRef  
 Incrementa el recuento de referencias del objeto string.  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Incrementa el recuento de referencias del objeto string.  
  
> [!NOTE]
>  No llame a este método en una cadena con un recuento de referencias negativo, ya que un número negativo indica que el búfer de cadena está bloqueado.  
  
##  <a name="data"></a>CStringData::data  
 Devuelve un puntero al búfer de caracteres de un objeto de cadena.  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al búfer de caracteres del objeto de cadena.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para devolver el búfer de caracteres actual del objeto de cadena asociado.  
  
> [!NOTE]
>  Este búfer no está asignado por el `CStringData` objeto pero el Administrador de la cadena cuando sea necesario. Cuando asigna, el búfer se anexa al objeto de datos de cadena.  
  
##  <a name="islocked"></a>CStringData::IsLocked  
 Determina si el búfer de caracteres está bloqueado.  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el búfer está bloqueado; de lo contrario **false**.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para determinar si el búfer de caracteres de un objeto de cadena se encuentra actualmente bloqueado.  
  
##  <a name="isshared"></a>CStringData::IsShared  
 Determina si se comparte el búfer de caracteres.  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el búfer es compartido; en caso contrario **false**.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para determinar si el búfer de caracteres de un objeto de datos de cadena actualmente se comparte entre varios objetos de cadena.  
  
##  <a name="lock"></a>CStringData::Lock  
 Bloquea el búfer de caracteres del objeto de cadena asociado.  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para bloquear el búfer de caracteres del objeto de datos de cadena. Bloqueo y desbloqueo se utilizan cuando el desarrollador requiere acceso directo al búfer de caracteres. Un buen ejemplo de bloqueo se demuestra la [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) métodos de `CSimpleStringT`.  
  
> [!NOTE]
>  Sólo se puede bloquear un búfer de caracteres si el búfer no se comparte entre los objetos de cadena superior.  
  
##  <a name="nalloclength"></a>CStringData::nAllocLength  
 Longitud del búfer de carácter asignado.  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>Comentarios  
 Almacena la longitud del búfer de datos asignado en `XCHAR`s (sin incluir el carácter nulo final).  
  
##  <a name="ndatalength"></a>CStringData::nDataLength  
 Longitud actual del objeto de cadena.  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>Comentarios  
 Almacena la longitud de datos actualmente utilizados en `XCHAR`s (sin incluir el carácter nulo final).  
  
##  <a name="nrefs"></a>CStringData::nRefs  
 Recuento de referencias del objeto de datos de cadena.  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>Comentarios  
 Almacena el recuento de referencias del objeto de datos de cadena. Este número indica el número de objetos de cadena superior que están asociados con el objeto de datos de cadena. Un valor negativo indica que el objeto de datos de cadena está bloqueado actualmente.  
  
##  <a name="pstringmgr"></a>CStringData::pStringMgr  
 El Administrador de memoria del objeto de cadena asociado.  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>Comentarios  
 Almacena el Administrador de memoria para el objeto de cadena asociado. Para obtener más información sobre cadenas y administradores de memoria, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="release"></a>CStringData::Release  
 Disminuye el recuento de referencias del objeto de datos de cadena.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para disminuir el recuento de referencias, liberando la `CStringData` estructura si el recuento de referencias llega a cero. Esto se suele hacer cuando se elimina un objeto de cadena y, por tanto, ya no necesita hacer referencia al objeto de datos de cadena.  
  
 Por ejemplo, el siguiente código llamaría `CStringData::Release` para el objeto de datos de cadena asociado con `str1`:  
  
 [!code-cpp[NVC_ATLMFC_Utilities&#104;](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="unlock"></a>CStringData::Unlock  
 Desbloquea el búfer de caracteres del objeto de cadena asociado.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para desbloquear el búfer de caracteres del objeto de datos de cadena. Cuando se desbloquea un búfer, es intercambiable y pueden ser recuento de referencias.  
  
> [!NOTE]
>  Cada llamada a `Lock` debe coincidir con una llamada correspondiente a `Unlock`.  
  
 Bloqueo y desbloqueo se utilizan cuando el programador debe asegurarse de que no se comparta los datos de cadena. Un buen ejemplo de bloqueo se demuestra la [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) métodos de `CSimpleStringT`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)



