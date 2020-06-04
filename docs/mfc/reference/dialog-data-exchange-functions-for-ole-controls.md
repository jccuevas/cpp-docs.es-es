---
title: Funciones de intercambio de datos de cuadro de diálogo para controles OLE
ms.date: 11/04/2016
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: 61a5983eec13902ed4b0e397e3befca4860977d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365766"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funciones de intercambio de datos de cuadro de diálogo para controles OLE

En este tema se enumeran las funciones DDX_OC utilizadas para intercambiar datos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos del cuadro de diálogo, vista de formulario o objeto de vista de control.

### <a name="ddx_oc-functions"></a>Funciones DDX_OC

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Administra la transferencia de datos **BOOL** entre una propiedad de un control OLE y un miembro de datos **BOOL.**|
|[DDX_OCBoolRO](#ddx_ocboolro)|Administra la transferencia de datos **BOOL** entre una propiedad de solo lectura de un control OLE y un miembro de datos **BOOL.**|
|[DDX_OCColor](#ddx_occolor)|Administra la transferencia de datos **OLE_COLOR** entre una propiedad de un control OLE y un miembro de datos **OLE_COLOR.**|
|[DDX_OCColorRO](#ddx_occolorro)|Administra la transferencia de datos **de OLE_COLOR** entre una propiedad de solo lectura de un control OLE y un miembro de datos **OLE_COLOR.**|
|[DDX_OCFloat](#ddx_ocfloat)|Administra la transferencia de datos **flotantes** (o **dobles)** entre una propiedad de un control OLE y un miembro de datos **float** (o **double).**|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Administra la transferencia de datos **flotantes** (o **dobles)** entre una propiedad de solo lectura de un control OLE y un miembro de datos **float** (o **double).**|
|[DDX_OCInt](#ddx_ocint)|Administra la transferencia de datos **int** (o **long)** entre una propiedad de un control OLE y un miembro de datos **int** (o **long).**|
|[DDX_OCIntRO](#ddx_ocintro)|Administra la transferencia de datos **int** (o **long)** entre una propiedad de solo lectura de un control OLE y un miembro de datos **int** (o **long).**|
|[DDX_OCShort](#ddx_ocshort)|Administra la transferencia de datos **cortos** entre una propiedad de un control OLE y un miembro de datos **cortos.**|
|[DDX_OCShortRO](#ddx_ocshortro)|Administra la transferencia de datos **cortos** entre una propiedad de solo lectura de un control OLE y un miembro de datos **corto.**|
|[DDX_OCText](#ddx_octext)|Administra la transferencia de datos de **CString** entre una propiedad de un control OLE y un miembro de datos **CString.**|
|[DDX_OCTextRO](#ddx_octextro)|Administra la transferencia de datos de **CString** entre una propiedad de solo lectura de un control OLE y un miembro de datos **CString.**|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

La `DDX_OCBool` función administra la transferencia de datos **BOOL** entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **BOOL** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado:** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

La `DDX_OCBoolRO` función administra la transferencia de datos **BOOL** entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **BOOL** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

La `DDX_OCColor` función administra la transferencia de datos OLE_COLOR entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos OLE_COLOR del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

La `DDX_OCColorRO` función administra la transferencia de datos de OLE_COLOR entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un OLE_COLOR miembro de datos del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

La `DDX_OCFloat` función administra la transferencia de datos **flotantes** (o **dobles)** entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **flotante** (o **doble)** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

La `DDX_OCFloatRO` función administra la transferencia de datos **flotantes** (o **dobles)** entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **flotante** (o **doble)** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

La `DDX_OCInt` función administra la transferencia de datos **int** (o **long)** entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **int** (o **long)** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

La `DDX_OCIntRO` función administra la transferencia de datos **int** (o **long)** entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **int** (o **long)** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

La `DDX_OCShort` función administra la transferencia de datos cortos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos cortos del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

La `DDX_OCShortRO` función administra la transferencia de datos cortos entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos cortos del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

La función **DDX_OCText** administra la transferencia de datos de **CString** entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **CString** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un **CDataExchange** objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a>DDX_OCTextRO

La función `DDX_OCTextRO` administra la transferencia de datos `CString` entre una propiedad de solo lectura de un control OLE de un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos `CString` del objeto de cuadro de dialogo, vista de formulario o vista de control.

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.

*dispid*<br/>
Identificador de envío de una propiedad del control.

*value*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
