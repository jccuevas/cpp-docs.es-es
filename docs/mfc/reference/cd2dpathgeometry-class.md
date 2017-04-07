---
title: Clase CD2DPathGeometry | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
dev_langs:
- C++
helpviewer_keywords:
- CD2DPathGeometry class
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
caps.latest.revision: 17
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
ms.openlocfilehash: 1c1158e55bf12d44f34896dd6752c9b8706db636
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dpathgeometry-class"></a>Clase CD2DPathGeometry
Un contenedor para ID2D1PathGeometry.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Construye un objeto CD2DPathGeometry.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DPathGeometry::Attach](#attach)|Conexiones existentes de la interfaz de recursos para el objeto|  
|[CD2DPathGeometry::Create](#create)|Crea un CD2DPathGeometry. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DPathGeometry::Destroy](#destroy)|Destruye un objeto CD2DPathGeometry. (Invalida [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|  
|[CD2DPathGeometry::Detach](#detach)|Separa la interfaz de recursos desde el objeto|  
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Recupera el número de figuras de la geometría de trayecto.|  
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Recupera el número de segmentos de la geometría de trayecto.|  
|[CD2DPathGeometry::Open](#open)|Recupera el receptor de geometría que se usa para rellenar la geometría de trayecto con figuras y segmentos.|  
|[CD2DPathGeometry::Stream](#stream)|Copia el contenido de la geometría de la ruta de acceso para el ID2D1GeometrySink especificado.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Puntero a un ID2D1PathGeometry.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 `CD2DPathGeometry`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="attach"></a>CD2DPathGeometry::Attach  
 Conexiones existentes de la interfaz de recursos para el objeto  
  
```  
void Attach(ID2D1PathGeometry* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry  
 Construye un objeto CD2DPathGeometry.  
  
```  
CD2DPathGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="create"></a>CD2DPathGeometry::Create  
 Crea un CD2DPathGeometry.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="destroy"></a>CD2DPathGeometry::Destroy  
 Destruye un objeto CD2DPathGeometry.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DPathGeometry::Detach  
 Separa la interfaz de recursos desde el objeto  
  
```  
ID2D1PathGeometry* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz desasociadas recursos.  
  
##  <a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount  
 Recupera el número de figuras de la geometría de trayecto.  
  
```  
int GetFigureCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de cifras de la geometría de trayecto.  
  
##  <a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount  
 Recupera el número de segmentos de la geometría de trayecto.  
  
```  
int GetSegmentCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de segmentos de la geometría de trayecto.  
  
##  <a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry  
 Puntero a un ID2D1PathGeometry.  
  
```  
ID2D1PathGeometry* m_pPathGeometry;  
```  
  
##  <a name="open"></a>CD2DPathGeometry::Open  
 Recupera el receptor de geometría que se usa para rellenar la geometría de trayecto con figuras y segmentos.  
  
```  
ID2D1GeometrySink* Open();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ID2D1GeometrySink que se usa para rellenar la geometría de trayecto con figuras y segmentos.  
  
##  <a name="stream"></a>CD2DPathGeometry::Stream  
 Copia el contenido de la geometría de la ruta de acceso para el ID2D1GeometrySink especificado.  
  
```  
BOOL Stream(ID2D1GeometrySink* geometrySink);
```  
  
### <a name="parameters"></a>Parámetros  
 `geometrySink`  
 El receptor al que se copia el contenido de la geometría de la ruta de acceso. Modificar este receptor no cambia el contenido de la geometría de la ruta de acceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

