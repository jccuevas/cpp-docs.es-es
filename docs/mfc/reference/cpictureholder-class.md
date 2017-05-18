---
title: Clase CPictureHolder | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- Picture property
- controls [MFC], OLE
- OLE controls, image
- CPictureHolder class
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
caps.latest.revision: 20
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 14a774e3edc8b5e160b287612d3709c3424503be
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cpictureholder-class"></a>CPictureHolder (clase)
Implementa una propiedad de imagen, que permite al usuario mostrar una imagen en el control.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPictureHolder  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPictureHolder::CPictureHolder](#cpictureholder)|Construye un objeto `CPictureHolder`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPictureHolder::CreateEmpty](#createempty)|Crea un objeto `CPictureHolder` vacío.|  
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Crea un `CPictureHolder` objeto de un mapa de bits.|  
|[CPictureHolder::CreateFromIcon](#createfromicon)|Crea un `CPictureHolder` objeto desde un icono.|  
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Crea un `CPictureHolder` objeto de un metarchivo.|  
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Recupera la cadena aparece en el Explorador de propiedades del contenedor del control.|  
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Devuelve el `CPictureHolder` del objeto `IDispatch` interfaz.|  
|[CPictureHolder::GetType](#gettype)|Indica si la `CPictureHolder` objeto es un mapa de bits, un metarchivo o icono.|  
|[CPictureHolder:: Render](#render)|Representa la imagen.|  
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Establece la `CPictureHolder` del objeto `IDispatch` interfaz.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPictureHolder::m_pPict](#m_ppict)|Puntero a un objeto de imagen.|  
  
## <a name="remarks"></a>Comentarios  
 `CPictureHolder`no tiene una clase base.  
  
 Con la propiedad de imagen estándar, el desarrollador puede especificar un mapa de bits, icono o metarchivo para su presentación.  
  
 Para obtener información sobre la creación de propiedades de la imagen personalizada, vea el artículo [controles ActiveX de MFC: utilizar imágenes en un ActiveX Control](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CPictureHolder`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="cpictureholder"></a>CPictureHolder::CPictureHolder  
 Construye un objeto `CPictureHolder`.  
  
```  
CPictureHolder();
```  
  
##  <a name="createempty"></a>CPictureHolder::CreateEmpty  
 Crea una cadena vacía `CPictureHolder` objeto y se conecta a un `IPicture` interfaz.  
  
```  
BOOL CreateEmpty();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario, 0.  
  
##  <a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap  
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
 `idResource`  
 Id. de recurso de un recurso de mapa de bits.  
  
 `pBitmap`  
 Puntero a un [CBitmap](../../mfc/reference/cbitmap-class.md) objeto.  
  
 *pPal*  
 Puntero a un [CPalette](../../mfc/reference/cpalette-class.md) objeto.  
  
 `bTransferOwnership`  
 Indica si el objeto de imagen tomará posesión de los objetos de mapa de bits y una paleta.  
  
 `hbm`  
 Identificador del mapa de bits a partir del que el `CPictureHolder` se crea el objeto.  
  
 `hpal`  
 Identificador de la paleta que se usa para representar el mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si `bTransferOwnership` es **TRUE**, el llamador no debe usar el mapa de bits o devuelve el objeto de la paleta de ninguna manera después de esta llamada. Si `bTransferOwnership` es **FALSE**, el llamador es responsable de garantizar que los objetos de mapa de bits y una paleta siguen siendo válidos durante la vigencia del objeto de imagen.  
  
##  <a name="createfromicon"></a>CPictureHolder::CreateFromIcon  
 Un icono que se utiliza para inicializar el objeto de imagen en un `CPictureHolder`.  
  
```  
BOOL CreateFromIcon(
    UINT idResource);

 
BOOL CreateFromIcon(
    HICON hIcon,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `idResource`  
 Id. de recurso de un recurso de mapa de bits.  
  
 `hIcon`  
 Identificador del icono a partir del que el `CPictureHolder` se crea el objeto.  
  
 `bTransferOwnership`  
 Indica si el objeto de imagen asumirá la propiedad del objeto de icono.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si `bTransferOwnership` es **TRUE**, el llamador no debe usar el objeto de icono de ninguna manera después de que esta llamada. Si `bTransferOwnership` es **FALSE**, el llamador es responsable de garantizar que el objeto de icono sigue siendo válido mientras dure el objeto de imagen.  
  
##  <a name="createfrommetafile"></a>CPictureHolder::CreateFromMetafile  
 Un metarchivo se utiliza para inicializar el objeto de imagen en un `CPictureHolder`.  
  
```  
BOOL CreateFromMetafile(
    HMETAFILE hmf,  
    int xExt,  
    int yExt,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `hmf`  
 Identificador del metarchivo que se utiliza para crear la `CPictureHolder` objeto.  
  
 *xExt*  
 X la extensión de la imagen.  
  
 *yExt*  
 Extensión Y de la imagen.  
  
 `bTransferOwnership`  
 Indica si el objeto de imagen asumirá la propiedad del objeto de metarchivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si `bTransferOwnership` es **TRUE**, el llamador no debe usar el objeto metarchivo de ninguna manera después de que esta llamada. Si `bTransferOwnership` es **FALSE**, el llamador es responsable de garantizar que el objeto de metarchivo sigue siendo válido mientras dure el objeto de imagen.  
  
##  <a name="getdisplaystring"></a>CPictureHolder::GetDisplayString  
 Recupera la cadena que se muestra en el Explorador de propiedades de un contenedor.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `strValue`  
 Hacer referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) que va a contener la cadena de presentación.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la cadena se recupera correctamente; en caso contrario, 0.  
  
##  <a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch  
 Esta función devuelve un puntero a la `CPictureHolder` del objeto `IPictureDisp` interfaz.  
  
```  
LPPICTUREDISP GetPictureDispatch();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CPictureHolder` del objeto `IPictureDisp` interfaz.  
  
### <a name="remarks"></a>Comentarios  
 El llamador debe llamar a **versión** en este puntero cuando haya terminado con él.  
  
##  <a name="gettype"></a>CPictureHolder::GetType  
 Indica si la imagen es un mapa de bits, metarchivo o icono.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que indica el tipo de la imagen. Los valores posibles y sus significados son los siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|**PICTYPE_UNINITIALIZED**|`CPictureHolder`objeto es unititialized.|  
|**PICTYPE_NONE**|`CPictureHolder`objeto está vacío.|  
|**PICTYPE_BITMAP**|La imagen es un mapa de bits.|  
|**PICTYPE_METAFILE**|La imagen es un metarchivo.|  
|**PICTYPE_ICON**|Imagen es un icono.|  
  
##  <a name="m_ppict"></a>CPictureHolder::m_pPict  
 Un puntero a la `CPictureHolder` del objeto `IPicture` interfaz.  
  
```  
LPPICTURE m_pPict;  
```  
  
##  <a name="render"></a>CPictureHolder:: Render  
 Representa la imagen en el rectángulo que se hace referencia a `rcRender`.  
  
```  
void Render(
    CDC* pDC,  
    const CRect& rcRender,  
    const CRect& rcWBounds);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero al contexto de presentación en la que la imagen se va a representar.  
  
 `rcRender`  
 Rectángulo en el que la imagen se va a representar.  
  
 *rcWBounds*  
 Un rectángulo que representa el rectángulo delimitador del objeto de representar la imagen. Para un control, este rectángulo es el `rcBounds` parámetro pasado a una invalidación de [COleControl:: OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).  
  
##  <a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch  
 Se conecta la `CPictureHolder` objeto un `IPictureDisp` interfaz.  
  
```  
void SetPictureDispatch(LPPICTUREDISP pDisp);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDisp`  
 Puntero a la nueva `IPictureDisp` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CFontHolder](../../mfc/reference/cfontholder-class.md)

