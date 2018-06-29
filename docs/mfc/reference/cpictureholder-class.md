---
title: Clase CPictureHolder | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
dev_langs:
- C++
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b81a35a696d3d5cdcb22a6f9a66425320b544c2
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079454"
---
# <a name="cpictureholder-class"></a>CPictureHolder (clase)
Implementa una propiedad de imagen, que permite al usuario mostrar una imagen en el control.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPictureHolder  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPictureHolder::CPictureHolder](#cpictureholder)|Construye un objeto `CPictureHolder`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPictureHolder::CreateEmpty](#createempty)|Crea un objeto `CPictureHolder` vacío.|  
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Crea un `CPictureHolder` objeto de un mapa de bits.|  
|[CPictureHolder::CreateFromIcon](#createfromicon)|Crea un `CPictureHolder` objeto desde un icono.|  
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Crea un `CPictureHolder` objeto desde un metarchivo.|  
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Recupera la cadena que se muestra en el Explorador de propiedades del contenedor del control.|  
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Devuelve el `CPictureHolder` del objeto `IDispatch` interfaz.|  
|[CPictureHolder::GetType](#gettype)|Indica si la `CPictureHolder` objeto es un mapa de bits, un metarchivo de o en un icono.|  
|[CPictureHolder:: Render](#render)|Representa la imagen.|  
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Establece el `CPictureHolder` del objeto `IDispatch` interfaz.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPictureHolder::m_pPict](#m_ppict)|Un puntero a un objeto de imagen.|  
  
## <a name="remarks"></a>Comentarios  
 `CPictureHolder` no tiene una clase base.  
  
 Con la propiedad de imagen estándar, el programador puede especificar un mapa de bits, icono o metarchivo para su presentación.  
  
 Para obtener información acerca de cómo crear propiedades de imagen personalizada, vea el artículo [controles ActiveX MFC: utilizar imágenes en un ActiveX Control](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CPictureHolder`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="cpictureholder"></a>  CPictureHolder::CPictureHolder  
 Construye un objeto `CPictureHolder`.  
  
```  
CPictureHolder();
```  
  
##  <a name="createempty"></a>  CPictureHolder::CreateEmpty  
 Crea vacío `CPictureHolder` objeto y se conecta a un `IPicture` interfaz.  
  
```  
BOOL CreateEmpty();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario es 0.  
  
##  <a name="createfrombitmap"></a>  CPictureHolder::CreateFromBitmap  
 Un mapa de bits se utiliza para inicializar el objeto de imagen en un `CPictureHolder`.  
  
```  
BOOL CreateFromBitmap(
    UINT idResource);

 
BOOL CreateFromBitmap(
    CBitmap* pBitmap,  
    CPalette* pPal = NULL,  
    BOOL bTransferOwnership = TRUE);

 
BOOL CreateFromBitmap(
    HBITMAP hbm,  
    HPALETTE hpal = NULL,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *idResource*  
 Id. de recurso de un recurso de mapa de bits.  
  
 *pBitmap*  
 Puntero a un [CBitmap](../../mfc/reference/cbitmap-class.md) objeto.  
  
 *pPal*  
 Puntero a un [CPalette](../../mfc/reference/cpalette-class.md) objeto.  
  
 *bTransferOwnership*  
 Indica si el objeto de imagen tomará posesión de los objetos de mapas de bits y una paleta.  
  
 *hbm*  
 Identificador para el mapa de bits a partir del que el `CPictureHolder` se crea el objeto.  
  
 *hpal*  
 Identificador de la paleta que se usa para representar el mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si *bTransferOwnership* es **TRUE**, el llamador no debe usar el mapa de bits o devuelve el objeto de la paleta de ninguna manera después de esta llamada. Si *bTransferOwnership* es **FALSE**, el llamador es responsable de garantizar que los objetos de mapas de bits y una paleta sigan siendo válidos para la duración del objeto de imagen.  
  
##  <a name="createfromicon"></a>  CPictureHolder::CreateFromIcon  
 Utiliza un icono para inicializar el objeto de imagen en un `CPictureHolder`.  
  
```  
BOOL CreateFromIcon(
    UINT idResource);

 
BOOL CreateFromIcon(
    HICON hIcon,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *idResource*  
 Id. de recurso de un recurso de mapa de bits.  
  
 *hIcon*  
 Identificador del icono a partir del que el `CPictureHolder` se crea el objeto.  
  
 *bTransferOwnership*  
 Indica si el objeto de imagen llevará a la propiedad del objeto de icono.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si *bTransferOwnership* es **TRUE**, el llamador no debe usar el objeto de icono de ninguna manera después de que esta llamada se devuelve. Si *bTransferOwnership* es **FALSE**, el llamador es responsable de garantizar que el objeto de icono sigue siendo válido durante la vigencia del objeto de imagen.  
  
##  <a name="createfrommetafile"></a>  CPictureHolder::CreateFromMetafile  
 Usa un metarchivo para inicializar el objeto de imagen en un `CPictureHolder`.  
  
```  
BOOL CreateFromMetafile(
    HMETAFILE hmf,  
    int xExt,  
    int yExt,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *hmf*  
 Identificador del metarchivo que se utiliza para crear la `CPictureHolder` objeto.  
  
 *xExt*  
 X alcance de la imagen.  
  
 *yExt*  
 Y el alcance de la imagen.  
  
 *bTransferOwnership*  
 Indica si el objeto de imagen llevará a la propiedad del objeto de metarchivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si *bTransferOwnership* es **TRUE**, el llamador no debe usar el objeto de metarchivo de ninguna manera después de que esta llamada se devuelve. Si *bTransferOwnership* es **FALSE**, el llamador es responsable de garantizar que el objeto de metarchivo sigue siendo válido durante la vigencia del objeto de imagen.  
  
##  <a name="getdisplaystring"></a>  CPictureHolder::GetDisplayString  
 Recupera la cadena que se muestra en el Explorador de propiedades de un contenedor.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *StrValue*  
 Referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) que va a contener la cadena de presentación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la cadena se ha recuperado correctamente; en caso contrario es 0.  
  
##  <a name="getpicturedispatch"></a>  CPictureHolder::GetPictureDispatch  
 Esta función devuelve un puntero a la `CPictureHolder` del objeto `IPictureDisp` interfaz.  
  
```  
LPPICTUREDISP GetPictureDispatch();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CPictureHolder` del objeto `IPictureDisp` interfaz.  
  
### <a name="remarks"></a>Comentarios  
 El llamador debe llamar a **versión** en este puntero cuando haya terminado con él.  
  
##  <a name="gettype"></a>  CPictureHolder::GetType  
 Indica si la imagen es un mapa de bits, un metarchivo o icono.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que indica el tipo de la imagen. Los valores posibles y sus significados son los siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|**PICTYPE_UNINITIALIZED**|`CPictureHolder` objeto es unititialized.|  
|**PICTYPE_NONE**|`CPictureHolder` objeto está vacío.|  
|**PICTYPE_BITMAP**|La imagen es un mapa de bits.|  
|**PICTYPE_METAFILE**|Imagen es un metarchivo.|  
|**PICTYPE_ICON**|Imagen es un icono.|  
  
##  <a name="m_ppict"></a>  CPictureHolder::m_pPict  
 Un puntero a la `CPictureHolder` del objeto `IPicture` interfaz.  
  
```  
LPPICTURE m_pPict;  
```  
  
##  <a name="render"></a>  CPictureHolder:: Render  
 Representa la imagen en el rectángulo al que hace referencia *rcRender*.  
  
```  
void Render(
    CDC* pDC,  
    const CRect& rcRender,  
    const CRect& rcWBounds);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDC*  
 Puntero para el contexto de presentación en la que se representará la imagen.  
  
 *rcRender*  
 Rectángulo en el que es la imagen que se representará.  
  
 *rcWBounds*  
 Un rectángulo que representa el rectángulo delimitador del objeto en la imagen de representación. Para un control, este rectángulo es el *rcBounds* parámetro pasado a una invalidación de [COleControl:: OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).  
  
##  <a name="setpicturedispatch"></a>  CPictureHolder::SetPictureDispatch  
 Se conecta la `CPictureHolder` el objeto a un `IPictureDisp` interfaz.  
  
```  
void SetPictureDispatch(LPPICTUREDISP pDisp);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDisp*  
 Puntero a la nueva `IPictureDisp` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFontHolder (clase)](../../mfc/reference/cfontholder-class.md)
