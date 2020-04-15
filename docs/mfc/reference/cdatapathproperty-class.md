---
title: Clase CDataPathProperty
ms.date: 11/04/2016
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
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: e96106dcd6f496c6cc99c9d72d86052547b6d06b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376465"
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
|[CDataPathProperty::GetControl](#getcontrol)|Recupera el control OLE asincrónico asociado al `CDataPathProperty` objeto.|
|[CDataPathProperty::GetPath](#getpath)|Recupera el nombre de ruta de acceso de la propiedad.|
|[CDataPathProperty::Open](#open)|Inicia la carga de la propiedad asincrónica para el control ActiveX (OLE) asociado.|
|[CDataPathProperty::ResetData](#resetdata)|Llamadas `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor que las propiedades del control han cambiado.|
|[CDataPathProperty::SetControl](#setcontrol)|Establece el control ActiveX asincrónico (OLE) asociado a la propiedad.|
|[CDataPathProperty::SetPath](#setpath)|Establece el nombre de ruta de acceso de la propiedad.|

## <a name="remarks"></a>Observaciones

Las propiedades asincrónicas se cargan después del inicio sincrónico.

La `CDataPathProperty` clase se `CAysncMonikerFile`deriva de . Para implementar propiedades asincrónicas en los `CDataPathProperty`controles OLE, derive una clase de , e invalide [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Para obtener más información acerca de cómo utilizar monikers asincrónicos y controles ActiveX en aplicaciones de Internet, consulte los siguientes artículos:

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

## <a name="cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty

Construye un objeto `CDataPathProperty`.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
Puntero al objeto de control OLE `CDataPathProperty` que se va a asociar a este objeto.

*lpszPath*<br/>
La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CDataPathProperty`utiliza direcciones URL, no nombres de archivo. Si desea `CDataPathProperty` un objeto para un `file://` archivo, anteponga la ruta de acceso.

### <a name="remarks"></a>Observaciones

El `COleControl` objeto señalado por *pControl* es utilizado por `Open` y recuperado por las clases derivadas. Si *pControl* es NULL, `Open` el control `SetControl`utilizado con debe establecerse con . Si *lpszPath* es NULL, puede pasar `Open` la ruta `SetPath`de acceso a través de ella o establecerla con .

## <a name="cdatapathpropertygetcontrol"></a><a name="getcontrol"></a>CDataPathProperty::GetControl

Llame a esta función miembro para recuperar el `COleControl` objeto asociado con el `CDataPathProperty` objeto.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al control `CDataPathProperty` OLE asociado al objeto. NULL si no se asocia el control.

## <a name="cdatapathpropertygetpath"></a><a name="getpath"></a>CDataPathProperty::GetPath

Llame a esta función miembro para `CDataPathProperty` recuperar la ruta de `Open`acceso, establecer cuando se construyó `SetPath` el objeto o se especificó en , o especificado en una llamada anterior a la función miembro.

```
CString GetPath() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el nombre de ruta de acceso a la propia propiedad. Puede estar vacío si no se ha especificado ninguna ruta de acceso.

## <a name="cdatapathpropertyopen"></a><a name="open"></a>CDataPathProperty::Open

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

*pControl*<br/>
Puntero al objeto de control OLE `CDataPathProperty` que se va a asociar a este objeto.

*pError*<br/>
Un puntero a una excepción de archivo. En caso de error, se establecerá en la causa.

*lpszPath*<br/>
La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CDataPathProperty`utiliza direcciones URL, no nombres de archivo. Si desea `CDataPathProperty` un objeto para un `file://` archivo, anteponga la ruta de acceso.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La función intenta `IBindHost` obtener la interfaz del control.

Antes `Open` de llamar sin una ruta de acceso, se debe establecer el valor de la ruta de acceso de la propiedad. Esto se puede hacer cuando se construye el `SetPath` objeto o mediante una llamada a la función miembro.

Antes `Open` de llamar sin un control, un control ActiveX (anteriormente conocido como un control OLE) se puede asociar con el objeto. Esto se puede hacer cuando se construye `SetControl`el objeto o llamando a .

Todas las sobrecargas de [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) también están disponibles desde `CDataPathProperty`.

## <a name="cdatapathpropertyresetdata"></a><a name="resetdata"></a>CDataPathProperty::ResetData

Llame a esta `CAsyncMonikerFile::OnDataAvailable` función para obtener para notificar al contenedor que las propiedades del control han cambiado y toda la información cargada de forma asincrónica ya no es útil.

```
virtual void ResetData();
```

### <a name="remarks"></a>Observaciones

La apertura debe reiniciarse. Las clases derivadas pueden invalidar esta función para diferentes valores predeterminados.

## <a name="cdatapathpropertysetcontrol"></a><a name="setcontrol"></a>CDataPathProperty::SetControl

Llame a esta función miembro para `CDataPathProperty` asociar un control OLE asincrónico con el objeto.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
Un puntero al control OLE asincrónico que se asociará a la propiedad.

## <a name="cdatapathpropertysetpath"></a><a name="setpath"></a>CDataPathProperty::SetPath

Llame a esta función miembro para establecer el nombre de ruta de la propiedad.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
Una ruta de acceso, que puede ser absoluta o relativa, a la propiedad que se carga de forma asincrónica. `CDataPathProperty`utiliza direcciones URL, no nombres de archivo. Si desea `CDataPathProperty` un objeto para un `file://` archivo, anteponga la ruta de acceso.

## <a name="see-also"></a>Consulte también

[Imagen de ejemplo MFC](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile (Clase)](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile (Clase)](../../mfc/reference/casyncmonikerfile-class.md)
