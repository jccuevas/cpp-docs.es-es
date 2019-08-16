---
title: Rutinas de intercambio de datos de cuadros de diálogo estándar
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 47586f9cff0fcbe2cd7bad31f3d93fed08190830
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511586"
---
# <a name="standard-dialog-data-exchange-routines"></a>Rutinas de intercambio de datos de cuadros de diálogo estándar

En este tema se enumeran las rutinas de intercambio de datos de cuadros de diálogo (DDX) estándar utilizadas para los controles de cuadro de diálogo comunes de MFC.

> [!NOTE]
>  Las rutinas de intercambio de datos de cuadros de diálogo estándar se definen en el archivo de encabezado afxdd_. h. Sin embargo, las aplicaciones deben incluir AFXWIN. h.

### <a name="ddx-functions"></a>Funciones DDX

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Inicializa o recupera el índice de la selección actual de un control de cuadro combinado.|
|[DDX_CBString](#ddx_cbstring)|Inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|
|[DDX_Check](#ddx_check)|Inicializa o recupera el estado actual de un control de casilla.|
|[DDX_Control](#ddx_control)|Subclasse un control determinado dentro de un cuadro de diálogo.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Inicializa o recupera datos de fecha y hora de un control selector de fecha y hora.|
|[DDX_IPAddress](#ddx_ipaddress)|Inicializa o recupera el valor actual de un control de dirección IP.|
|[DDX_LBIndex](#ddx_lbindex)|Inicializa o recupera el índice de la selección actual de un control de cuadro de lista.|
|[DDX_LBString](#ddx_lbstring)|Inicializa o recupera la selección actual dentro de un control de cuadro de lista.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Inicializa o recupera la selección actual dentro de un control de cuadro de lista.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Crea un control .NET que coincide con el identificador de recurso del control.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Inicializa o recupera el valor actual de un control de calendario mensual.|
|[DDX_Radio](#ddx_radio)|Inicializa o recupera el índice de base cero del control de radio que está activado actualmente dentro de un grupo de control de radio.|
|[DDX_Scroll](#ddx_scroll)|Inicializa o recupera la posición actual del control de desplazamiento.|
|[DDX_Slider](#ddx_slider)|Inicializa o recupera la posición actual del control de un control deslizante.|
|[DDX_Text](#ddx_text)|Inicializa o recupera el valor actual de un control de edición.|

##  <a name="ddx_cbindex"></a>  DDX_CBIndex

La `DDX_CBIndex` función administra la transferencia de datos **int** entre un control de cuadro combinado en un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos **int** del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de cuadro combinado asociado a la propiedad de control.

*index*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_CBIndex` se llama a, *index* se establece en el índice de la selección del cuadro combinado actual. Si no hay ningún elemento seleccionado, el *Índice* se establece en 0.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_cbstring"></a>  DDX_CBString

La `DDX_CBString` función administra la transferencia de `CString` datos entre el control de edición de un control de cuadro combinado en un objeto de cuadro de diálogo, vista de formulario o `CString` vista de control y un miembro de datos del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de cuadro combinado asociado a la propiedad de control.

*value*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_CBString` se llama a, el *valor* se establece en la selección del cuadro combinado actual. Si no hay ningún elemento seleccionado, el *valor* se establece en una cadena de longitud cero.

> [!NOTE]
>  Si el cuadro combinado es un cuadro de lista desplegable, el valor intercambiado se limita a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact

La `DDX_CBStringExact` función administra la transferencia de `CString` datos entre el control de edición de un control de cuadro combinado en un objeto de cuadro de diálogo, vista de formulario o `CString` vista de control y un miembro de datos del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de cuadro combinado asociado a la propiedad de control.

*value*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_CBStringExact` se llama a, el *valor* se establece en la selección del cuadro combinado actual. Si no hay ningún elemento seleccionado, el *valor* se establece en una cadena de longitud cero.

> [!NOTE]
>  Si el cuadro combinado es un cuadro de lista desplegable, el valor intercambiado se limita a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_check"></a>DDX_Check

La `DDX_Check` función administra la transferencia de datos **int** entre un control de casilla en un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos **int** del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de casilla asociado a la propiedad de control.

*value*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_Check` se llama a, el *valor* se establece en el estado actual del control de casilla. Para obtener una lista de los valores de estado posibles, vea [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) en el Windows SDK.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_control"></a>DDX_Control

La `DDX_Control` función subclase el control, especificado por *nIDC*, del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*nIDC*<br/>
IDENTIFICADOR de recurso del control del que se van a crear subclases.

*rControl*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control relacionada con el control especificado.

### <a name="remarks"></a>Comentarios

El marco de trabajo suministra el objeto *pDX* cuando se `DoDataExchange` llama a la función. Por lo `DDX_Control` tanto, solo se debe llamar dentro de `DoDataExchange`la invalidación de.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl

La `DDX_DateTimeCtrl` función administra la transferencia de datos de fecha y hora entre un control de selector de fecha y hora ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) de un cuadro de diálogo o un objeto de vista de formulario y un miembro de datos [ctime](../../atl-mfc-shared/reference/ctime-class.md) o [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) del cuadro de diálogo o formulario. objeto de vista.

```
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
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar este objeto.

*nIDC*<br/>
IDENTIFICADOR de recurso del control selector de fecha y hora asociado a la variable miembro.

*value*<br/>
En las dos primeras versiones, una referencia a una `CTime` variable `COleDateTime` miembro de o, un cuadro de diálogo, una vista de formulario o un objeto de vista de control con el que se intercambian los datos. En la tercera versión, referencia a un `CString` objeto de vista de control de miembro de datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_DateTimeCtrl` se llama a, el *valor* se establece en el estado actual del control selector de fecha y hora, o el control se establece en *Value*, dependiendo de la dirección del intercambio.

En la tercera versión anterior, `DDX_DateTimeCtrl` administra la transferencia de `CString` datos entre un control de fecha y hora y un miembro de datos [CString](../../atl-mfc-shared/reference/cstringt-class.md) del objeto de vista de control. Se aplica formato a la cadena mediante las reglas de la configuración regional actual para dar formato a las fechas y horas.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

## <a name="ddx_managedcontrol"></a>DDX_ManagedControl

Crea un control .NET que coincide con el identificador de recurso del control.

### <a name="syntax"></a>Sintaxis

```
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto de la [clase CDataExchange (](cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control asociado a la propiedad de control.

*control*<br/>
Referencia a un objeto de la [clase CWinFormsControl](cwinformscontrol-class.md) .

### <a name="remarks"></a>Comentarios

`DDX_ManagedControl`llama a [CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) para crear un control que coincida con el identificador de control de recursos. Use `DDX_ManagedControl` para crear controles a partir de los identificadores de recursos en [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog). Para el intercambio de datos, no es necesario usar las funciones DDX/DDV con controles de Windows Forms.

Para obtener más información, consulte [Cómo Realice el enlace de datos DDX/DDV](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)con Windows Forms.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms. h

##  <a name="ddx_ipaddress"></a>  DDX_IPAddress

La `DDX_IPAddress` función administra la transferencia de datos entre un control de dirección IP y un miembro de datos del objeto de vista de control.

```
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de dirección IP asociado a la propiedad de control.

*value*<br/>
Referencia a la DWORD que contiene el valor de cuatro campos del control de dirección IP. Los campos se rellenan o se leen como se indica a continuación.

|Campo|Bits que contiene el valor del campo|
|-----------|-------------------------------------|
|3|de 0 a 7|
|2|de 8 a 15|
|1|de 16 a 23|
|0|de 24 a 31|

Use el [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) de Win32 para leer el valor o use [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) para rellenar el valor. Estos mensajes se describen en el Windows SDK.

### <a name="remarks"></a>Comentarios

Cuando `DDX_IPAddress` se llama a, el *valor* se lee desde el control de dirección IP o el *valor* se escribe en el control, en función de la dirección del intercambio.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_lbindex"></a>DDX_LBIndex

La `DDX_LBIndex` función administra la transferencia de datos **int** entre un control de cuadro de lista en un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos **int** del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de cuadro de lista asociado a la propiedad de control.

*index*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_LBIndex` se llama a, *index* se establece en el índice de la selección del cuadro de lista actual. Si no hay ningún elemento seleccionado, *index* se establece en-1.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_lbstring"></a>  DDX_LBString

La `DDX_LBString` función administra la transferencia de `CString` datos entre un control de cuadro de lista en un objeto de cuadro de diálogo, vista de formulario o `CString` vista de control y un miembro de datos del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de cuadro de lista asociado a la propiedad de control.

*value*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_LBString` se llama a para transferir datos a un control de cuadro de lista, se selecciona el primer elemento del control cuyo *valor* de inicio coincide. (Para que coincida con todo el elemento en lugar de simplemente un prefijo, use [DDX_LBStringExact](#ddx_lbstringexact)). Si no hay ninguna coincidencia, no se selecciona ningún elemento. La coincidencia no distingue entre mayúsculas y minúsculas.

Cuando `DDX_LBString` se llama a para transferir datos de un control de cuadro de lista, el *valor* se establece en la selección actual del cuadro de lista. Si no hay ningún elemento seleccionado, el *valor* se establece en una cadena de longitud cero.

> [!NOTE]
>  Si el cuadro de lista es un cuadro de lista desplegable, el valor intercambiado se limita a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact

La `DDX_CBStringExact` función administra la transferencia de `CString` datos entre el control de edición de un control de cuadro de lista en un objeto de cuadro de diálogo, vista de formulario `CString` o vista de control y un miembro de datos del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de cuadro de lista asociado a la propiedad de control.

*value*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_LBStringExact` se llama a para transferir datos a un control de cuadro de lista, se selecciona el primer elemento del control que coincida con el *valor* . (Para que coincida solo con un prefijo en lugar de con todo el elemento, use [DDX_LBString](#ddx_lbstring)). Si no hay ninguna coincidencia, no se selecciona ningún elemento. La coincidencia no distingue entre mayúsculas y minúsculas.

Cuando `DDX_CBStringExact` se llama a para transferir datos de un control de cuadro de lista, el *valor* se establece en la selección actual del cuadro de lista. Si no hay ningún elemento seleccionado, el *valor* se establece en una cadena de longitud cero.

> [!NOTE]
>  Si el cuadro de lista es un cuadro de lista desplegable, el valor intercambiado se limita a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl

La `DDX_MonthCalCtrl` función administra la transferencia de datos de fecha entre un control de calendario mensual ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) en un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos [ctime](../../atl-mfc-shared/reference/ctime-class.md) o [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) del cuadro de diálogo, formulario vista o objeto de vista de control.

```
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
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar este objeto.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de calendario mensual asociado a la variable miembro.

*value*<br/>
Referencia a una `CTime` variable o `COleDateTime` miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  El control solo administra un valor de fecha. Los campos de hora del objeto de hora se establecen para reflejar la hora de creación de la ventana de control, o cualquier hora establecida en el control con una `CMonthCalCtrl::SetCurSel`llamada a.

Cuando `DDX_MonthCalCtrl` se llama a, el *valor* se establece en el estado actual del control de calendario mensual.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_radio"></a>  DDX_Radio

La `DDX_Radio` función administra la transferencia de datos **int** entre un grupo de control de radio en un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos **int** del objeto de cuadro de diálogo, vista de formulario o vista de control. El valor del miembro de datos **int** se determina según el botón de radio del grupo seleccionado.

```
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del primer control de radio del grupo.

*value*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_Radio` se llama a, el *valor* se establece en el estado actual del grupo de control de radio. El valor se establece como un índice de base cero del control de radio que está activado actualmente, o-1 si no se comprueba ningún control de radio.

Por ejemplo, en caso de que se compruebe el primer botón de radio del grupo (el botón con el estilo WS_GROUP), el valor del miembro **int** es 0 y así sucesivamente.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_scroll"></a>  DDX_Scroll

La `DDX_Scroll` función administra la transferencia de datos **int** entre un control de barra de desplazamiento en un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos **int** del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de barra de desplazamiento asociado a la propiedad de control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_Scroll` se llama a, el *valor* se establece en la posición actual del control de posición del control. Para obtener más información sobre los valores asociados a la posición actual del control Thumb del control, vea [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) en el Windows SDK.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_slider"></a>  DDX_Slider

La `DDX_Slider` función administra la transferencia de datos **int** entre un control deslizante de un cuadro de diálogo o una vista de formulario y un miembro de datos **int** del cuadro de diálogo o el objeto de vista de formulario.

```
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control deslizante.

*value*<br/>
Referencia al valor que se va a intercambiar. Este parámetro contiene o establece la posición actual del control deslizante.

### <a name="remarks"></a>Comentarios

Cuando `DDX_Slider` se llama a, el *valor* se establece en la posición actual del control de posición del control o el valor recibe la posición, dependiendo de la dirección del intercambio.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener información acerca de los controles deslizantes, vea [usar CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

##  <a name="ddx_text"></a>  DDX_Text

La `DDX_Text` función administra la transferencia de datos **int**, **uint**, **Long**, DWORD `CString`,, **float**o **Double** entre un control de edición en un cuadro de diálogo, vista de formulario o vista de control y datos de [CString](../../atl-mfc-shared/reference/cstringt-class.md) . miembro del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
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
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de un control de edición en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*value*<br/>
Referencia a un miembro de datos en el objeto de cuadro de diálogo, vista de formulario o vista de control. El tipo de datos del *valor* depende de las versiones sobrecargadas de `DDX_Text` que use.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_. h

## <a name="see-also"></a>Vea también

[Rutinas de validación de datos de cuadro de diálogo estándar](standard-dialog-data-validation-routines.md)<br/>
[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
