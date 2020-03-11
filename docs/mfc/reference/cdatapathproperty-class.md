---
title: CDataPathProperty (clase)
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
ms.openlocfilehash: 89cb8ddcdd42643f52f755516e8845109163c57a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890829"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty (clase)

Implementa una propiedad de control OLE que se puede cargar de forma asincrónica.

## <a name="syntax"></a>Sintaxis

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDataPathProperty:: CDataPathProperty](#cdatapathproperty)|Construye un objeto `CDataPathProperty`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDataPathProperty:: GetControl](#getcontrol)|Recupera el control OLE asincrónico asociado al objeto `CDataPathProperty`.|
|[CDataPathProperty:: GetPath](#getpath)|Recupera la ruta de la propiedad.|
|[CDataPathProperty:: Open](#open)|Inicia la carga de la propiedad asincrónica para el control ActiveX (OLE) asociado.|
|[CDataPathProperty:: ResetData](#resetdata)|Llama a `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor que las propiedades del control han cambiado.|
|[CDataPathProperty:: SetControl](#setcontrol)|Establece el control ActiveX (OLE) asincrónico asociado a la propiedad.|
|[CDataPathProperty:: SetPath](#setpath)|Establece la ruta de la propiedad.|

## <a name="remarks"></a>Observaciones

Las propiedades asincrónicas se cargan después del inicio sincrónico.

La clase `CDataPathProperty` se deriva de `CAysncMonikerFile`. Para implementar propiedades asincrónicas en los controles OLE, derive una clase de `CDataPathProperty`e invalide [ondataavailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Para obtener más información sobre cómo usar monikers asincrónicos y controles ActiveX en aplicaciones de Internet, vea los siguientes artículos:

- [Primeros pasos de Internet: controles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Primeros pasos de Internet: monikers asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxctl. h

##  <a name="cdatapathproperty"></a>CDataPathProperty:: CDataPathProperty

Construye un objeto `CDataPathProperty`.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
Puntero al objeto de control OLE que se va a asociar a este objeto `CDataPathProperty`.

*lpszPath*<br/>
La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que haga referencia a la ubicación absoluta real de la propiedad. `CDataPathProperty` usa direcciones URL, no nombres de archivo. Si desea un objeto de `CDataPathProperty` para un archivo, anteponga `file://` a la ruta de acceso.

### <a name="remarks"></a>Observaciones

`Open` usa el `COleControl` objeto al que apunta *pControl* y lo recuperan las clases derivadas. Si *pControl* es null, el control utilizado con `Open` se debe establecer con `SetControl`. Si *lpszPath* es null, puede pasar la ruta de acceso a través de `Open` o establecerla con `SetPath`.

##  <a name="getcontrol"></a>CDataPathProperty:: GetControl

Llame a esta función miembro para recuperar el objeto de `COleControl` asociado al objeto `CDataPathProperty`.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al control OLE asociado al objeto `CDataPathProperty`. Es NULL si no hay ningún control asociado.

##  <a name="getpath"></a>CDataPathProperty:: GetPath

Llame a esta función miembro para recuperar la ruta de acceso, establezca cuándo se construyó el `CDataPathProperty` objeto o si se especificó en `Open`o si se especificó en una llamada anterior a la función miembro `SetPath`.

```
CString GetPath() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el directorio de la propiedad en sí. Puede estar vacío si no se ha especificado ninguna ruta de acceso.

##  <a name="open"></a>CDataPathProperty:: Open

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
Puntero al objeto de control OLE que se va a asociar a este objeto `CDataPathProperty`.

*pError*<br/>
Puntero a una excepción de archivo. En caso de que se produzca un error, se establecerá en la causa.

*lpszPath*<br/>
La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que haga referencia a la ubicación absoluta real de la propiedad. `CDataPathProperty` usa direcciones URL, no nombres de archivo. Si desea un objeto de `CDataPathProperty` para un archivo, anteponga `file://` a la ruta de acceso.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La función intenta obtener la interfaz de `IBindHost` del control.

Antes de llamar a `Open` sin una ruta de acceso, debe establecerse el valor de la ruta de acceso de la propiedad. Esto se puede hacer cuando se construye el objeto o llamando a la función miembro `SetPath`.

Antes de llamar a `Open` sin un control, se puede asociar un control ActiveX (antes conocido como control OLE) al objeto. Esto se puede hacer cuando se construye el objeto o llamando a `SetControl`.

Todas las sobrecargas de [CAsyncMonikerFile:: Open](../../mfc/reference/casyncmonikerfile-class.md#open) también están disponibles en `CDataPathProperty`.

##  <a name="resetdata"></a>CDataPathProperty:: ResetData

Llame a esta función para obtener `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor que las propiedades del control han cambiado y toda la información cargada de forma asincrónica ya no es útil.

```
virtual void ResetData();
```

### <a name="remarks"></a>Observaciones

Se debe reiniciar la apertura. Las clases derivadas pueden invalidar esta función para los distintos valores predeterminados.

##  <a name="setcontrol"></a>CDataPathProperty:: SetControl

Llame a esta función miembro para asociar un control OLE asincrónico al objeto `CDataPathProperty`.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
Puntero al control OLE asincrónico que se va a asociar a la propiedad.

##  <a name="setpath"></a>CDataPathProperty:: SetPath

Llame a esta función miembro para establecer la ruta de la propiedad.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
Una ruta de acceso, que puede ser absoluta o relativa, a la propiedad que se carga de forma asincrónica. `CDataPathProperty` usa direcciones URL, no nombres de archivo. Si desea un objeto de `CDataPathProperty` para un archivo, anteponga `file://` a la ruta de acceso.

## <a name="see-also"></a>Consulte también

[Imagen de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile (clase)](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile (clase)](../../mfc/reference/casyncmonikerfile-class.md)
