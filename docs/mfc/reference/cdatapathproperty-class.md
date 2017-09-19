---
title: Clase CDataPathProperty | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- ActiveX controls [C++], asynchronous
- OLE controls [C++], asynchronous
- CDataPathProperty class
- asynchronous controls [C++]
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
caps.latest.revision: 24
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
ms.openlocfilehash: d767cf950d8b86959aadc2fd4d77401134a6dc75
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cdatapathproperty-class"></a>Clase CDataPathProperty
Implementa una propiedad de control OLE que se puede cargar de forma asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Construye un objeto `CDataPathProperty`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|Recupera el control asincrónico de OLE asociado a la `CDataPathProperty` objeto.|  
|[CDataPathProperty::GetPath](#getpath)|Recupera la ruta de acceso de la propiedad.|  
|[CDataPathProperty::Open](#open)|Inicializa la carga de la propiedad asincrónica del control ActiveX (OLE).|  
|[CDataPathProperty::ResetData](#resetdata)|Llamadas `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor que han cambiado las propiedades del control.|  
|[CDataPathProperty::SetControl](#setcontrol)|Establece el control ActiveX (OLE) asincrónica asociado a la propiedad.|  
|[CDataPathProperty::SetPath](#setpath)|Establece la ruta de acceso de la propiedad.|  
  
## <a name="remarks"></a>Comentarios  
 Propiedades asincrónicas se cargan después de un inicio sincrónico.  
  
 La clase `CDataPathProperty` se deriva de **CAysncMonikerFile**. Para implementar propiedades asincrónicas en controles OLE, derive una clase de `CDataPathProperty`e invalidar [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).  
  
 Para obtener más información acerca de cómo utilizar controles ActiveX y monikers asincrónicos en aplicaciones de Internet, consulte los artículos siguientes:  
  
- [Primeros pasos de Internet: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Primeros pasos de Internet: Monikers asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty  
 Construye un objeto `CDataPathProperty`.  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pControl`  
 Un puntero al objeto de control OLE que se asociará con este `CDataPathProperty` objeto.  
  
 `lpszPath`  
 La ruta de acceso, que puede ser absoluta o relativa, se utiliza para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CDataPathProperty`utiliza direcciones URL, no nombres de archivo. Si desea un `CDataPathProperty` de objeto para un archivo, anteponga `file://` a la ruta de acceso.  
  
### <a name="remarks"></a>Comentarios  
 El `COleControl` objeto señalado por `pControl` utiliza **abiertos** y recuperar las clases derivadas. Si `pControl` es **NULL**, el control se utiliza con **abiertos** debe establecerse con `SetControl`. Si `lpszPath` es **NULL**, puede pasar la ruta de acceso a través de **abiertos** o con `SetPath`.  
  
##  <a name="getcontrol"></a>CDataPathProperty::GetControl  
 Llame a esta función miembro para recuperar el `COleControl` objeto asociado a la `CDataPathProperty` objeto.  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al control OLE asociado con el `CDataPathProperty` objeto. **NULL** si el control no está asociado.  
  
##  <a name="getpath"></a>CDataPathProperty::GetPath  
 Llame a esta función miembro para recuperar la ruta de acceso, establecer cuando la `CDataPathProperty` objeto se crea o se especificó en **abiertos**, o se ha especificado en una llamada anterior a la `SetPath` función miembro.  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la ruta de acceso a la propiedad en Sí. Puede estar vacío si no se ha especificado ninguna ruta de acceso.  
  
##  <a name="open"></a>CDataPathProperty::Open  
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
 `pControl`  
 Un puntero al objeto de control OLE que se asociará con este `CDataPathProperty` objeto.  
  
 `pError`  
 Un puntero a una excepción de archivo. Si se produce un error, establecerá la causa del problema.  
  
 `lpszPath`  
 La ruta de acceso, que puede ser absoluta o relativa, se utiliza para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CDataPathProperty`utiliza direcciones URL, no nombres de archivo. Si desea un `CDataPathProperty` de objeto para un archivo, anteponga `file://` a la ruta de acceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La función intenta obtener la `IBindHost` interfaz desde el control.  
  
 Antes de llamar a **abiertos** sin una ruta de acceso, se debe establecer el valor de ruta de acceso de la propiedad. Esto puede hacerse cuando el objeto está construido, o mediante una llamada a la `SetPath` función miembro.  
  
 Antes de llamar a **abiertos** sin un control, un control ActiveX (anteriormente conocido como un control OLE) puede asociarse con el objeto. Esto puede hacerse cuando el objeto está construido, o mediante una llamada a `SetControl`.  
  
 Todas las sobrecargas de [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) también están disponibles en `CDataPathProperty`.  
  
##  <a name="resetdata"></a>CDataPathProperty::ResetData  
 Llame a esta función para obtener `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor que han cambiado las propiedades del control, y toda la información que se cargan de forma asincrónica ya no es útil.  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>Comentarios  
 Apertura debe reiniciarse. Las clases derivadas pueden reemplazar esta función para distintos valores predeterminados.  
  
##  <a name="setcontrol"></a>CDataPathProperty::SetControl  
 Llame a esta función miembro para asociar un control OLE asincrónico con la `CDataPathProperty` objeto.  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>Parámetros  
 `pControl`  
 Un puntero al control OLE asincrónica que se asociará con la propiedad.  
  
##  <a name="setpath"></a>CDataPathProperty::SetPath  
 Llame a esta función miembro para establecer la ruta de acceso de la propiedad.  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPath`  
 Una ruta de acceso, que puede ser absoluta o relativa a la propiedad que se va a cargar de forma asincrónica. `CDataPathProperty`utiliza direcciones URL, no nombres de archivo. Si desea un `CDataPathProperty` de objeto para un archivo, anteponga `file://` a la ruta de acceso.  
  
## <a name="see-also"></a>Vea también  
 [Imagen de ejemplo MFC](../../visual-cpp-samples.md)   
 [Clase CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

