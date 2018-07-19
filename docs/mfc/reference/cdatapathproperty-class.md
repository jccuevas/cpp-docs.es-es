---
title: CDataPathProperty (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
dev_langs:
- C++
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 164742ea39f92194a3354ae24a90eeff9512f59c
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335976"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty (clase)
Implementa una propiedad de control OLE que se puede cargar de forma asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Construye un objeto `CDataPathProperty`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|Recupera el control OLE asincrónico asociado con el `CDataPathProperty` objeto.|  
|[CDataPathProperty::GetPath](#getpath)|Recupera la ruta de acceso de la propiedad.|  
|[CDataPathProperty::Open](#open)|Inicia la carga de la propiedad asincrónica para el control ActiveX (OLE) asociado.|  
|[CDataPathProperty::ResetData](#resetdata)|Las llamadas `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor que han cambiado las propiedades del control.|  
|[CDataPathProperty::SetControl](#setcontrol)|Establece el control ActiveX (OLE) asincrónica asociado a la propiedad.|  
|[CDataPathProperty::SetPath](#setpath)|Establece la ruta de acceso de la propiedad.|  
  
## <a name="remarks"></a>Comentarios  
 Propiedades asincrónicas se cargan después de un inicio sincrónico.  
  
 La clase `CDataPathProperty` se deriva de `CAysncMonikerFile`. Para implementar propiedades asincrónicas en los controles OLE, derive una clase de `CDataPathProperty`e invalidar [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).  
  
 Para obtener más información sobre cómo usar controles ActiveX y monikers asincrónicos en aplicaciones de Internet, consulte los artículos siguientes:  
  
- [Internet primeros pasos: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet primeros pasos: Monikers asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty  
 Construye un objeto `CDataPathProperty`.  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pControl*  
 Un puntero al objeto de control OLE que se asociará con este `CDataPathProperty` objeto.  
  
 *lpszPath*  
 La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CDataPathProperty` usa las direcciones URL, no los nombres de archivo. Si desea que un `CDataPathProperty` para un archivo de objeto, anteponga `file://` a la ruta de acceso.  
  
### <a name="remarks"></a>Comentarios  
 El `COleControl` objeto señalado por *pControl* usa `Open` y recuperados por las clases derivadas. Si *pControl* es NULL, el control usado con `Open` debe establecerse con `SetControl`. Si *lpszPath* es NULL, puede pasar en la ruta de acceso a través de `Open` o establecerlo con `SetPath`.  
  
##  <a name="getcontrol"></a>  CDataPathProperty::GetControl  
 Llame a esta función miembro para recuperar el `COleControl` objeto asociado con el `CDataPathProperty` objeto.  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al control OLE asociado con el `CDataPathProperty` objeto. NULL si no control está asociado.  
  
##  <a name="getpath"></a>  CDataPathProperty::GetPath  
 Llame a esta función miembro para recuperar la ruta de acceso, se establece cuando el `CDataPathProperty` objeto se construye o se especificó en `Open`, o se ha especificado en una llamada anterior a la `SetPath` función miembro.  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la ruta de acceso a la propiedad propiamente dicha. Puede estar vacío si no se ha especificado ninguna ruta de acceso.  
  
##  <a name="open"></a>  CDataPathProperty::Open  
 Llame a esta función miembro para iniciar la carga de la propiedad asincrónica para el control asociado.  
  
```  
virtual BOOL Open(
    COleControl* pControl,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    COleControl* pControl,
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    CFileException* pError = NULL);  
  
virtual BOOL Open(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pControl*  
 Un puntero al objeto de control OLE que se asociará con este `CDataPathProperty` objeto.  
  
 *pError*  
 Un puntero a una excepción de archivo. Si se produce un error, se establecerá la causa.  
  
 *lpszPath*  
 La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CDataPathProperty` usa las direcciones URL, no los nombres de archivo. Si desea que un `CDataPathProperty` para un archivo de objeto, anteponga `file://` a la ruta de acceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La función intenta obtener el `IBindHost` interfaz desde el control.  
  
 Antes de llamar a `Open` sin una ruta de acceso, se debe establecer el valor de ruta de acceso de la propiedad. Esto puede hacerse cuando el objeto está construido, o mediante una llamada a la `SetPath` función miembro.  
  
 Antes de llamar a `Open` sin un control, se puede asociar con el objeto de un control ActiveX (conocido anteriormente como un control OLE). Esto puede hacerse cuando el objeto está construido, o mediante una llamada a `SetControl`.  
  
 Todas las sobrecargas de [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) también están disponibles en `CDataPathProperty`.  
  
##  <a name="resetdata"></a>  CDataPathProperty::ResetData  
 Llame a esta función para obtener `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor que han cambiado las propiedades del control, y ya no es útil toda la información que se cargan de forma asincrónica.  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>Comentarios  
 Apertura debe reiniciarse. Las clases derivadas pueden reemplazar esta función para distintos valores predeterminados.  
  
##  <a name="setcontrol"></a>  CDataPathProperty::SetControl  
 Llame a esta función miembro para asociar un control OLE asincrónico con el `CDataPathProperty` objeto.  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>Parámetros  
 *pControl*  
 Un puntero al control OLE asincrónica que se asociará con la propiedad.  
  
##  <a name="setpath"></a>  CDataPathProperty::SetPath  
 Llame a esta función miembro para establecer la ruta de acceso de la propiedad.  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszPath*  
 Una ruta de acceso, que puede ser absoluta o relativa a la propiedad que se va a cargar de forma asincrónica. `CDataPathProperty` usa las direcciones URL, no los nombres de archivo. Si desea que un `CDataPathProperty` para un archivo de objeto, anteponga `file://` a la ruta de acceso.  
  
## <a name="see-also"></a>Vea también  
 [Imagen de ejemplo MFC](../../visual-cpp-samples.md)   
 [CAsyncMonikerFile (clase)](../../mfc/reference/casyncmonikerfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile (clase)](../../mfc/reference/casyncmonikerfile-class.md)
