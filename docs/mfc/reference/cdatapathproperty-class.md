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
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4f258f5872a68931a40d21f7079e4089678baac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdatapathproperty-class"></a>Clase CDataPathProperty
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
|[CDataPathProperty::GetControl](#getcontrol)|Recupera el control OLE asincrónico asociado a la `CDataPathProperty` objeto.|  
|[CDataPathProperty::GetPath](#getpath)|Recupera la ruta de acceso de la propiedad.|  
|[CDataPathProperty::Open](#open)|Inicia la carga de la propiedad asincrónica para el control ActiveX (OLE) asociado.|  
|[CDataPathProperty::ResetData](#resetdata)|Llamadas `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor que han cambiado las propiedades del control.|  
|[CDataPathProperty::SetControl](#setcontrol)|Establece el control ActiveX (OLE) asincrónica asociado a la propiedad.|  
|[CDataPathProperty::SetPath](#setpath)|Establece la ruta de acceso de la propiedad.|  
  
## <a name="remarks"></a>Comentarios  
 Propiedades asincrónicas se cargan después de un inicio sincrónico.  
  
 La clase `CDataPathProperty` se deriva de **CAysncMonikerFile**. Para implementar propiedades asincrónicas en los controles OLE, derive una clase de `CDataPathProperty`e invalidar [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).  
  
 Para obtener más información sobre cómo usar controles de ActiveX y monikers asincrónicos en las aplicaciones de Internet, consulte los artículos siguientes:  
  
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
 La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que hace referencia a la ubicación real absoluta de la propiedad. `CDataPathProperty`usa las direcciones URL, no los nombres de archivo. Si desea que un `CDataPathProperty` de objetos para un archivo, anteponga `file://` a la ruta de acceso.  
  
### <a name="remarks"></a>Comentarios  
 El `COleControl` objeto señalado por `pControl` utiliza **abiertos** y recuperar las clases derivadas. Si `pControl` es **NULL**, el control que se utiliza con **abiertos** debe establecerse con `SetControl`. Si `lpszPath` es **NULL**, se puede pasar en la ruta de acceso a través de **abiertos** o establézcalo con `SetPath`.  
  
##  <a name="getcontrol"></a>CDataPathProperty::GetControl  
 Llame a esta función miembro para recuperar el `COleControl` objeto asociado a la `CDataPathProperty` objeto.  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al control OLE asociado con el `CDataPathProperty` objeto. **NULL** si el control no está asociado.  
  
##  <a name="getpath"></a>CDataPathProperty::GetPath  
 Llame a esta función miembro para recuperar la ruta de acceso, establecer cuando la `CDataPathProperty` objeto se construye o se especificó en **abiertos**, o se ha especificado en una llamada anterior a la `SetPath` función miembro.  
  
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
 Un puntero a una excepción de archivo. Si se produce un error, se establecerá en la causa.  
  
 `lpszPath`  
 La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que hace referencia a la ubicación real absoluta de la propiedad. `CDataPathProperty`usa las direcciones URL, no los nombres de archivo. Si desea que un `CDataPathProperty` de objetos para un archivo, anteponga `file://` a la ruta de acceso.  
  
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
 Apertura debe reiniciarse. Las clases derivadas pueden invalidar esta función para valores predeterminados diferentes.  
  
##  <a name="setcontrol"></a>CDataPathProperty::SetControl  
 Llame a esta función miembro para asociar un control OLE asincrónico con el `CDataPathProperty` objeto.  
  
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
 Una ruta de acceso, que puede ser absoluta o relativa a la propiedad que se va a cargar de forma asincrónica. `CDataPathProperty`usa las direcciones URL, no los nombres de archivo. Si desea que un `CDataPathProperty` de objetos para un archivo, anteponga `file://` a la ruta de acceso.  
  
## <a name="see-also"></a>Vea también  
 [Imagen de ejemplo MFC](../../visual-cpp-samples.md)   
 [Clase CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile (clase)](../../mfc/reference/casyncmonikerfile-class.md)
