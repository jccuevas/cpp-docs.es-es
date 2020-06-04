---
title: Rutinas de intercambio de datos de cuadros de diálogo estándar
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 83d4a66cd3ec41008506b55f0b351fd9bcbc24b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372930"
---
# <a name="standard-dialog-data-exchange-routines"></a>Rutinas de intercambio de datos de cuadros de diálogo estándar

En este tema se enumeran las rutinas de intercambio de datos de cuadro de diálogo estándar (DDX) utilizadas para los controles de cuadro de diálogo MFC comunes.

> [!NOTE]
> Las rutinas de intercambio de datos de cuadro de diálogo estándar se definen en el archivo de cabecera afxdd_.h. Sin embargo, las aplicaciones deben incluir afxwin.h.

### <a name="ddx-functions"></a>Funciones DDX

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Inicializa o recupera el índice de la selección actual de un control de cuadro combinado.|
|[DDX_CBString](#ddx_cbstring)|Inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|
|[DDX_Check](#ddx_check)|Inicializa o recupera el estado actual de un control de casilla de verificación.|
|[DDX_Control](#ddx_control)|Subclases de un control determinado dentro de un cuadro de diálogo.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Inicializa o recupera datos de fecha y/o hora de un control de selector de fecha y hora.|
|[DDX_IPAddress](#ddx_ipaddress)|Inicializa o recupera el valor actual de un control de dirección IP.|
|[DDX_LBIndex](#ddx_lbindex)|Inicializa o recupera el índice de la selección actual de un control de cuadro de lista.|
|[DDX_LBString](#ddx_lbstring)|Inicializa o recupera la selección actual dentro de un control de cuadro de lista.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Inicializa o recupera la selección actual dentro de un control de cuadro de lista.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Crea un control .NET que coincide con el identificador de recurso del control.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Inicializa o recupera el valor actual de un control de calendario de mes.|
|[DDX_Radio](#ddx_radio)|Inicializa o recupera el índice basado en 0 del control de radio que se comprueba actualmente dentro de un grupo de control de radio.|
|[DDX_Scroll](#ddx_scroll)|Inicializa o recupera la posición actual del pulgar de un control de desplazamiento.|
|[DDX_Slider](#ddx_slider)|Inicializa o recupera la posición actual del pulgar de un control deslizante.|
|[DDX_Text](#ddx_text)|Inicializa o recupera el valor actual de un control de edición.|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex

La `DDX_CBIndex` función administra la transferencia de datos **int** entre un control de cuadro combinado en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **int** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de cuadro combinado asociado a la propiedad de control.

*índice*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_CBIndex` se llama, *index* se establece en el índice de la selección actual del cuadro combinado. Si no se selecciona ningún elemento, *index* se establece en 0.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a>DDX_CBString

La `DDX_CBString` función administra `CString` la transferencia de datos entre el control de edición de un `CString` control de cuadro combinado en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de cuadro combinado asociado a la propiedad de control.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_CBString` se llama, *value* se establece en la selección actual del cuadro combinado. Si no se selecciona ningún elemento, *el valor* se establece en una cadena de longitud cero.

> [!NOTE]
> Si el cuadro combinado es un cuadro de lista desplegable, el valor intercambiado está limitado a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact

La `DDX_CBStringExact` función administra `CString` la transferencia de datos entre el control de edición de un `CString` control de cuadro combinado en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de cuadro combinado asociado a la propiedad de control.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_CBStringExact` se llama, *value* se establece en la selección actual del cuadro combinado. Si no se selecciona ningún elemento, *el valor* se establece en una cadena de longitud cero.

> [!NOTE]
> Si el cuadro combinado es un cuadro de lista desplegable, el valor intercambiado está limitado a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_check"></a><a name="ddx_check"></a>DDX_Check

La `DDX_Check` función administra la transferencia de datos **int** entre un control de casilla de verificación en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **int** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de casilla de verificación asociado a la propiedad de control.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_Check` se llama, *value* se establece en el estado actual del control de casilla de verificación. Para obtener una lista de los posibles valores de estado, consulte [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) en el Windows SDK.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_control"></a><a name="ddx_control"></a>DDX_Control

La `DDX_Control` función subclases del control, especificado por *nIDC*, del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*nIDC*<br/>
El identificador de recurso del control que se va a subclase.

*rControl*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control relacionado con el control especificado.

### <a name="remarks"></a>Observaciones

El marco de trabajo proporciona el `DoDataExchange` objeto *pDX* cuando se llama a la función. Por `DDX_Control` lo tanto, solo se `DoDataExchange`debe llamar dentro de la invalidación de .

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

La `DDX_DateTimeCtrl` función administra la transferencia de datos de fecha y/o hora entre un control de selector de fecha y hora ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) en un cuadro de diálogo o un objeto de vista de formulario y un [CTime](../../atl-mfc-shared/reference/ctime-class.md) o un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) miembro de datos del cuadro de diálogo o objeto de vista de formulario.

```cpp
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar este objeto.

*nIDC*<br/>
El identificador de recurso del control de selector de fecha y hora asociado a la variable miembro.

*value*<br/>
En las dos primeras versiones, una referencia a una `CTime` variable o `COleDateTime` miembro, cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos. En la tercera versión, `CString` una referencia a un objeto de vista de control de miembro de datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_DateTimeCtrl` se llama, *value* se establece en el estado actual del control selector de fecha y hora, o el control se establece en *value*, dependiendo de la dirección del intercambio.

En la tercera `DDX_DateTimeCtrl` versión anterior, administra la transferencia de `CString` datos entre un control de fecha y hora y un Miembro de datos [CString](../../atl-mfc-shared/reference/cstringt-class.md) del objeto de vista de control. La cadena tiene formato mediante las reglas de configuración regional actual para dar formato a fechas y horas.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a>DDX_ManagedControl

Crea un control .NET que coincide con el identificador de recurso del control.

### <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange clase](cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control asociado a la propiedad de control.

*Control*<br/>
Una referencia a un [CWinFormsControl clase](cwinformscontrol-class.md) objeto.

### <a name="remarks"></a>Observaciones

`DDX_ManagedControl`llama a [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) para crear un control que coincida con el identificador de control de recursos. Se `DDX_ManagedControl` utiliza para crear controles a partir de identificadores de recursos en [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Para el intercambio de datos, no es necesario utilizar las funciones DDX/DDV con controles de formularios Windows Forms.

Para obtener más información, vea Cómo: Hacer enlace de [datos DDX/DDV con formularios Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress

La `DDX_IPAddress` función gestiona la transferencia de datos entre un control de dirección IP y un miembro de datos del objeto de vista de control.

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de dirección IP asociado a la propiedad de control.

*value*<br/>
Una referencia a la DWORD que contiene el valor de cuatro campos del control de dirección IP. Los campos se rellenan o se leen de la siguiente manera.

|Campo|Bits que contienen el valor del campo|
|-----------|-------------------------------------|
|3|0 a 7|
|2|8 a 15|
|1|16 a 23|
|0|24 a 31|

Utilice el [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) Win32 para leer el valor o utilice [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) para rellenar el valor. Estos mensajes se describen en el Windows SDK.

### <a name="remarks"></a>Observaciones

Cuando `DDX_IPAddress` se llama, *el valor* se lee desde el control de dirección IP o el *valor* se escribe en el control, dependiendo de la dirección del intercambio.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex

La `DDX_LBIndex` función administra la transferencia de datos **int** entre un control de cuadro de lista en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **int** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de cuadro de lista asociado a la propiedad de control.

*índice*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_LBIndex` se llama, *index* se establece en el índice de la selección actual del cuadro de lista. Si no se selecciona ningún elemento, *index* se establece en -1.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a>DDX_LBString

La `DDX_LBString` función administra `CString` la transferencia de datos entre un control de cuadro de `CString` lista en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de cuadro de lista asociado a la propiedad de control.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_LBString` se llama para transferir datos a un control de cuadro de lista, se selecciona el primer elemento del control cuyo *valor* de coincidencias iniciales. (Para que coincida con todo el elemento en lugar de solo un prefijo, utilice [DDX_LBStringExact](#ddx_lbstringexact).) Si no hay coincidencias, no se selecciona ningún elemento. La coincidencia no distingue mayúsculas de minúsculas.

Cuando `DDX_LBString` se llama para transferir datos desde un control de cuadro de lista, *value* se establece en la selección de cuadro de lista actual. Si no se selecciona ningún elemento, *el valor* se establece en una cadena de longitud cero.

> [!NOTE]
> Si el cuadro de lista es un cuadro de lista desplegable, el valor intercambiado está limitado a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact

La `DDX_CBStringExact` función administra `CString` la transferencia de datos entre el control de edición de un `CString` control de cuadro de lista en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de cuadro de lista asociado a la propiedad de control.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_LBStringExact` se llama para transferir datos a un control de cuadro de lista, se selecciona el primer elemento del control que coincide con *el valor.* (Para que coincida con solo un prefijo en lugar de todo el elemento, utilice [DDX_LBString](#ddx_lbstring).) Si no hay coincidencias, no se selecciona ningún elemento. La coincidencia no distingue mayúsculas de minúsculas.

Cuando `DDX_CBStringExact` se llama para transferir datos desde un control de cuadro de lista, *value* se establece en la selección de cuadro de lista actual. Si no se selecciona ningún elemento, *el valor* se establece en una cadena de longitud cero.

> [!NOTE]
> Si el cuadro de lista es un cuadro de lista desplegable, el valor intercambiado está limitado a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

La `DDX_MonthCalCtrl` función administra la transferencia de datos de fecha entre un control de calendario de mes ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) en un cuadro de diálogo, vista de formulario o objeto de vista de control y un [CTime](../../atl-mfc-shared/reference/ctime-class.md) o un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) miembro de datos del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar este objeto.

*nIDC*<br/>
El identificador de recurso del control de calendario de mes asociado a la variable miembro.

*value*<br/>
Una referencia `CTime` a `COleDateTime` una variable o variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> El control solo administra un valor de fecha. Los campos de tiempo del objeto time se establecen para reflejar el tiempo de creación `CMonthCalCtrl::SetCurSel`de la ventana de control o cualquier hora establecida en el control con una llamada a .

Cuando `DDX_MonthCalCtrl` se llama, *value* se establece en el estado actual del control de calendario del mes.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_radio"></a><a name="ddx_radio"></a>DDX_Radio

La `DDX_Radio` función administra la transferencia de datos **int** entre un grupo de control de radio en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **int** del cuadro de diálogo, vista de formulario o objeto de vista de control. El valor del miembro de datos **int** se determina según el botón de opción dentro del grupo seleccionado.

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El ID de recurso del primer control de radio del grupo.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_Radio` se llama, *el valor* se establece en el estado actual del grupo de control de radio. El valor se establece como un índice basado en 0 del control de radio que está marcado actualmente, o -1 si no se comprueba ningún control de radio.

Por ejemplo, en caso de que se compruebe el primer botón de opción del grupo (el botón con estilo WS_GROUP) el valor del miembro **int** es 0 y así sucesivamente.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a>DDX_Scroll

La `DDX_Scroll` función administra la transferencia de datos **int** entre un control de barra de desplazamiento en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **int** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de barra de desplazamiento asociado a la propiedad de control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_Scroll` se llama, *value* se establece en la posición actual del pulgar del control. Para obtener más información sobre los valores asociados con la posición actual del control, vea [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) en el Windows SDK.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_slider"></a><a name="ddx_slider"></a>DDX_Slider

La `DDX_Slider` función administra la transferencia de datos **int** entre un control deslizante en un cuadro de diálogo o vista de formulario y un miembro de datos **int** del cuadro de diálogo o del objeto de vista de formulario.

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control deslizante.

*value*<br/>
Una referencia al valor que se va a intercambiar. Este parámetro mantiene o establece la posición actual del control deslizante.

### <a name="remarks"></a>Observaciones

Cuando `DDX_Slider` se llama, *value* se establece en la posición actual del pulgar del control, o el valor recibe la posición, dependiendo de la dirección del intercambio.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener información acerca de los controles deslizantes, consulte Uso de [CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_text"></a><a name="ddx_text"></a>DDX_Text

La `DDX_Text` función administra la transferencia de datos **int** `CString`, **UINT**, **long**, DWORD, , **float**o **double** entre un control de edición en un cuadro de diálogo, vista de formulario o vista de control y un miembro de datos [CString](../../atl-mfc-shared/reference/cstringt-class.md) del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control de edición en el cuadro de diálogo, la vista de formulario o el objeto de vista de control.

*value*<br/>
Una referencia a un miembro de datos en el cuadro de diálogo, la vista de formulario o el objeto de vista de control. El tipo de datos de *valor* depende `DDX_Text` de cuál de las versiones sobrecargadas de uso.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="see-also"></a>Consulte también

[Rutinas de validación de datos de cuadro de diálogo estándar](standard-dialog-data-validation-routines.md)<br/>
[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
