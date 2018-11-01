---
title: Rutinas de intercambio de datos de cuadros de diálogo estándar
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 06153a72ce6ed6e5422022255eec333110709778
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618314"
---
# <a name="standard-dialog-data-exchange-routines"></a>Rutinas de intercambio de datos de cuadros de diálogo estándar

En este tema se enumera las rutinas de exchange (DDX) de datos de cuadro de diálogo estándar utilizadas para los controles de cuadro de diálogo comunes de MFC.

> [!NOTE]
>  Las rutinas de intercambio de datos de cuadro de diálogo estándar se definen en el afxdd_.h del archivo de encabezado. Sin embargo, las aplicaciones deben incluir afxwin.h.

### <a name="ddx-functions"></a>DDX (funciones)

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Inicializa o recupera el índice de la selección actual de un control de cuadro combinado.|
|[DDX_CBString](#ddx_cbstring)|Inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|
|[DDX_Check](#ddx_check)|Inicializa o recupera el estado actual de un control de casilla de verificación.|
|[DDX_Control](#ddx_control)|Subclases de un control determinado dentro de un cuadro de diálogo.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Inicializa o recupera datos de fecha u hora de un control de selector de fecha y hora.|
|[DDX_IPAddress](#ddx_ipaddress)|Inicializa o recupera el valor actual de un control de dirección IP.|
|[DDX_LBIndex](#ddx_lbindex)|Inicializa o recupera el índice de la selección actual de un control de cuadro de lista.|
|[DDX_LBString](#ddx_lbstring)|Inicializa o recupera la selección actual en un control de cuadro de lista.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Inicializa o recupera la selección actual en un control de cuadro de lista.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Crea un control de .NET que coincida con identificador de recurso. del control|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Inicializa o recupera el valor actual de un control de calendario mensual.|
|[DDX_Radio](#ddx_radio)|Inicializa o recupera el índice de base 0 del control de radio que está actualmente activado dentro de un grupo de control de radio.|
|[DDX_Scroll](#ddx_scroll)|Inicializa o recupera la posición actual del control de posición de un control de desplazamiento.|
|[DDX_Slider](#ddx_slider)|Inicializa o recupera la posición actual del control de posición de un control deslizante.|
|[DDX_Text](#ddx_text)|Inicializa o recupera el valor actual de un control de edición.|

##  <a name="ddx_cbindex"></a>  DDX_CBIndex

El `DDX_CBIndex` administra la transferencia de la función **int** datos entre un control de cuadro combinado en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **int** miembro de datos del cuadro de diálogo, vista de formulario o control objeto de vista.

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
El identificador de recurso de control de cuadro combinado asociado con la propiedad del control.

*index*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

Cuando `DDX_CBIndex` se llama, *índice* se establece en el índice de la selección actual del cuadro combinado. Si se selecciona ningún elemento, *índice* se establece en 0.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_cbstring"></a>  DDX_CBString

El `DDX_CBString` administra la transferencia de la función `CString` datos entre el control de edición de un control de cuadro combinado en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `CString` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

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
El identificador de recurso de control de cuadro combinado asociado con la propiedad del control.

*valor*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

Cuando `DDX_CBString` se llama, *valor* está establecido en la selección actual del cuadro combinado. Si se selecciona ningún elemento, *valor* se establece en una cadena de longitud cero.

> [!NOTE]
>  Si el cuadro combinado es un cuadro de lista desplegable, el valor que se intercambian está limitado a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact

El `DDX_CBStringExact` administra la transferencia de la función `CString` datos entre el control de edición de un control de cuadro combinado en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `CString` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

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
El identificador de recurso de control de cuadro combinado asociado con la propiedad del control.

*valor*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

Cuando `DDX_CBStringExact` se llama, *valor* está establecido en la selección actual del cuadro combinado. Si se selecciona ningún elemento, *valor* se establece en una cadena de longitud cero.

> [!NOTE]
>  Si el cuadro combinado es un cuadro de lista desplegable, el valor que se intercambian está limitado a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_check"></a>  DDX_Check

El `DDX_Check` administra la transferencia de la función **int** datos entre un control de casilla de verificación en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **int** miembro de datos del cuadro de diálogo, vista de formulario o control objeto de vista.

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
El identificador de recurso del control de casilla de verificación asociado con la propiedad del control.

*valor*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

Cuando `DDX_Check` se llama, *valor* está establecido en el estado actual del control de casilla de verificación. Para obtener una lista de los valores de los Estados posibles, consulte [BM_GETCHECK](/windows/desktop/Controls/bm-getcheck) en el SDK de Windows.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_control"></a>  DDX_Control

El `DDX_Control` función subclases en el control, especificado por *nIDC*, del cuadro de diálogo, vista de formulario o del objeto de vista de control.

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*nIDC*<br/>
El identificador de recurso del control que se pueden crear subclases.

*rControl*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o relacionados con el control especificado el objeto de vista de control.

### <a name="remarks"></a>Comentarios

El *pDX* objeto proporcionado por el marco de trabajo cuando el `DoDataExchange` se llama a la función. Por lo tanto, `DDX_Control` solo debe llamarse dentro de la invalidación de `DoDataExchange`.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl

El `DDX_DateTimeCtrl` función administra la transferencia de datos de fecha u hora entre un control de selector de fecha y hora ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) en un objeto de vista de formulario o de cuadro de diálogo y, o bien un [CTime](../../atl-mfc-shared/reference/ctime-class.md) o un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) miembro de datos del objeto de vista de formulario o de cuadro de diálogo.

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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar este objeto.

*nIDC*<br/>
El identificador de recurso del control de selector de fecha y hora asociado con la variable de miembro.

*valor*<br/>
En las dos primeras versiones, una referencia a un `CTime` o `COleDateTime` variable miembro, cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control. En la tercera versión, una referencia a un `CString` objeto de vista de control de miembro de datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_DateTimeCtrl` se llama, *valor* está establecido en el actual estado de la fecha y control de selector de hora o el control se establece en *valor*, según la dirección del intercambio.

En la tercera versión anterior, `DDX_DateTimeCtrl` administra la transferencia de `CString` control datos entre una fecha y hora y un [CString](../../atl-mfc-shared/reference/cstringt-class.md) miembro de datos del objeto de vista de control. Formato de la cadena mediante las reglas de la configuración regional actual para dar formato a fechas y horas.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddx_managedcontrol"></a>  DDX_ManagedControl

Crea un control de .NET que coincida con identificador de recurso. del control

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
Un puntero a un [CDataExchange (clase)](cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control asociado con la propiedad del control.

*control*<br/>
Una referencia a un [CWinFormsControl (clase)](cwinformscontrol-class.md) objeto.

### <a name="remarks"></a>Comentarios

`DDX_ManagedControl` las llamadas [CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) para crear un control que coincida con el identificador de control de recursos. Use `DDX_ManagedControl` para crear controles de identificadores de recursos en [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog). Intercambio de datos, no es necesario utilizar las funciones DDX/DDV con controles de formularios Windows Forms.

Para obtener más información, consulte [Cómo: realizar enlace de datos DDX/DDV con formularios de Windows](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h

### <a name="see-also"></a>Vea también

[CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog:: OnInitDialog](cdialog-class.md#oninitdialog)

##  <a name="ddx_ipaddress"></a>  DDX_IPAddress

El `DDX_IPAddress` función administra la transferencia de datos entre un control de dirección IP y un miembro de datos del objeto de vista de control.

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
El identificador de recurso del control de dirección IP asociado con la propiedad del control.

*valor*<br/>
Una referencia para el valor DWORD que contiene el valor del campo de cuatro del control de dirección IP. Los campos se rellenan o se quede como sigue.

|Campo|Que contiene el valor del campo de bits|
|-----------|-------------------------------------|
|3|de 0 a 7|
|2|8 a 15|
|1|16 a 23|
|0|24 a 31|

Utilizar Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress) para leer el valor, o use [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress) para rellenar el valor. Estos mensajes se describen en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Cuando `DDX_IPAddress` se llama, *valor* se lee desde el control de dirección IP, o *valor* se escribe en el control, dependiendo de la dirección del intercambio.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_lbindex"></a>  DDX_LBIndex

El `DDX_LBIndex` administra la transferencia de la función **int** datos entre un control de cuadro de lista en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **int** miembro de datos del cuadro de diálogo, vista de formulario o control objeto de vista.

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
El identificador de recurso del control de cuadro de lista asociado con la propiedad del control.

*index*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

Cuando `DDX_LBIndex` se llama, *índice* se establece en el índice de la selección actual del cuadro de lista. Si se selecciona ningún elemento, *índice* se establece en -1.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_lbstring"></a>  DDX_LBString

El `DDX_LBString` administra la transferencia de la función `CString` datos entre un control de cuadro de lista en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `CString` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

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
El identificador de recurso del control de cuadro de lista asociado con la propiedad del control.

*valor*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

Cuando `DDX_LBString` se llama para transferir datos a un control de cuadro de lista, el primer elemento en el control cuyo principio coincide con *valor* está seleccionada. (Para que coincida con el elemento entero en lugar de simplemente un prefijo, utilice [DDX_LBStringExact](#ddx_lbstringexact).) Si no hay ninguna coincidencia, no hay elementos seleccionados. La coincidencia distingue entre mayúsculas y minúsculas.

Cuando `DDX_LBString` se llama para transferir datos desde un control de cuadro de lista, *valor* está establecido en la selección actual del cuadro de lista. Si se selecciona ningún elemento, *valor* se establece en una cadena de longitud cero.

> [!NOTE]
>  Si el cuadro de lista es un cuadro de lista desplegable, el valor que se intercambian está limitado a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact

El `DDX_CBStringExact` administra la transferencia de la función `CString` datos entre el control de edición de un control de cuadro de lista en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `CString` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

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
El identificador de recurso del control de cuadro de lista asociado con la propiedad del control.

*valor*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

Cuando `DDX_LBStringExact` se llama para transferir datos a un control de cuadro de lista, el primer elemento en el control que coincida con *valor* está seleccionada. (Para que coincida solo con un prefijo en lugar del elemento completo, use [DDX_LBString](#ddx_lbstring).) Si no hay ninguna coincidencia, no hay elementos seleccionados. La coincidencia distingue entre mayúsculas y minúsculas.

Cuando `DDX_CBStringExact` se llama para transferir datos desde un control de cuadro de lista, *valor* está establecido en la selección actual del cuadro de lista. Si se selecciona ningún elemento, *valor* se establece en una cadena de longitud cero.

> [!NOTE]
>  Si el cuadro de lista es un cuadro de lista desplegable, el valor que se intercambian está limitado a 255 caracteres.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl

El `DDX_MonthCalCtrl` función administra la transferencia de datos de fecha entre un control de calendario mensual ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) en un cuadro de diálogo, vista de formulario, o el objeto de vista de control y un [CTime](../../atl-mfc-shared/reference/ctime-class.md) o un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar este objeto.

*nIDC*<br/>
El identificador de recurso de control de calendario mensual asociada con la variable de miembro.

*valor*<br/>
Una referencia a un `CTime` o `COleDateTime` variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  El control administra solo un valor de fecha. Los campos de tiempo en el objeto de tiempo son conjunto para reflejar la hora de creación de la ventana de control o cualquier momento se estableció en el control con una llamada a `CMonthCalCtrl::SetCurSel`.

Cuando `DDX_MonthCalCtrl` se llama, *valor* está establecido en el estado actual del control de calendario mensual.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_radio"></a>  DDX_Radio

El `DDX_Radio` administra la transferencia de la función **int** datos entre un grupo de control de radio en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **int** miembro de datos del cuadro de diálogo, vista de formulario o control objeto de vista. El valor de la **int** miembro de datos se determina según qué opción se selecciona el botón dentro del grupo.

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
El identificador de recurso del primer control de radio del grupo.

*valor*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

### <a name="remarks"></a>Comentarios

Cuando `DDX_Radio` se llama, *valor* está establecido en el estado actual del grupo de control de radio. El valor se establece como un índice de base 0 del control de radio que está actualmente activado, o -1 si ningún control de radio se comprueban.

Por ejemplo, en caso de que el primer botón de radio del grupo está activado (el botón con el estilo WS_GROUP) el valor de la **int** miembro es 0, y así sucesivamente.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_scroll"></a>  DDX_Scroll

El `DDX_Scroll` administra la transferencia de la función **int** datos entre un control de barra de desplazamiento en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **int** miembro de datos del cuadro de diálogo, vista de formulario o control objeto de vista.

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
El identificador de recurso del control de barra de desplazamiento asociado con la propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Cuando `DDX_Scroll` se llama, *valor* se establece en la posición actual del control de posición del control. Para obtener más información sobre los valores asociados con la posición actual del control de posición del control, vea [GetScrollPos](/windows/desktop/api/winuser/nf-winuser-getscrollpos) en el SDK de Windows.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_slider"></a>  DDX_Slider

El `DDX_Slider` administra la transferencia de la función **int** datos entre un control deslizante en una vista de formulario o de cuadro de diálogo y un **int** miembro de datos del objeto de vista de formulario o de cuadro de diálogo.

```
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

*valor*<br/>
Una referencia al valor que se van a intercambiar. Este parámetro contiene o establece la posición actual del control deslizante.

### <a name="remarks"></a>Comentarios

Cuando `DDX_Slider` se llama, *valor* se establece en la posición actual del control de posición del control, o el valor recibe la posición, dependiendo de la dirección del intercambio.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener información acerca de los controles deslizantes, consulte [usar CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddx_text"></a>  DDX_Text

El `DDX_Text` administra la transferencia de la función **int**, **UINT**, **largo**, DWORD, `CString`, **float**, o **doble** datos entre un control de edición en un cuadro de diálogo, vista de formulario o vista de control y un [CString](../../atl-mfc-shared/reference/cstringt-class.md) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control de edición en el cuadro de diálogo, vista de formulario o el objeto de vista de control.

*valor*<br/>
Una referencia a un miembro de datos en el cuadro de diálogo, vista de formulario o el objeto de vista de control. Tipo de datos de *valor* dependerá de cuál de las versiones sobrecargadas de `DDX_Text` utilice.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="see-also"></a>Vea también

[Rutinas de validación de datos de cuadro de diálogo estándar](../../mfc/reference/standard-dialog-data-validation-routines.md)<br/>
[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
