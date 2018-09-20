---
title: Funciones de intercambio de datos de cuadro de diálogo para controles OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a24bac5e27b0a3e0b1c011b1bb6019be2160d281
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382315"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funciones de intercambio de datos de cuadro de diálogo para controles OLE

Este tema enumeran las funciones DDX_OC utilizadas para intercambiar datos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

### <a name="ddxoc-functions"></a>Funciones DDX_OC

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Administra la transferencia de **BOOL** datos entre una propiedad de un control OLE y un **BOOL** miembro de datos.|
|[DDX_OCBoolRO](#ddx_ocboolro)|Administra la transferencia de **BOOL** datos entre una propiedad de solo lectura de un control OLE y un **BOOL** miembro de datos.|
|[DDX_OCColor](#ddx_occolor)|Administra la transferencia de **OLE_COLOR** datos entre una propiedad de un control OLE y un **OLE_COLOR** miembro de datos.|
|[DDX_OCColorRO](#ddx_occolorro)|Administra la transferencia de **OLE_COLOR** datos entre una propiedad de solo lectura de un control OLE y un **OLE_COLOR** miembro de datos.|
|[DDX_OCFloat](#ddx_ocfloat)|Administra la transferencia de **float** (o **doble**) datos entre una propiedad de un control OLE y un **float** (o **doble**) miembro de datos.|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Administra la transferencia de **float** (o **doble**) datos entre una propiedad de solo lectura de un control OLE y un **float** (o **doble**) datos miembro.|
|[DDX_OCInt](#ddx_ocint)|Administra la transferencia de **int** (o **largo**) datos entre una propiedad de un control OLE y un **int** (o **largo**) miembro de datos.|
|[DDX_OCIntRO](#ddx_ocintro)|Administra la transferencia de **int** (o **largo**) datos entre una propiedad de solo lectura de un control OLE y un **int** (o **largo**) miembro de datos.|
|[DDX_OCShort](#ddx_ocshort)|Administra la transferencia de **corto** datos entre una propiedad de un control OLE y un **corto** miembro de datos.|
|[DDX_OCShortRO](#ddx_ocshortro)|Administra la transferencia de **corto** datos entre una propiedad de solo lectura de un control OLE y un **corto** miembro de datos.|
|[DDX_OCText](#ddx_octext)|Administra la transferencia de **CString** datos entre una propiedad de un control OLE y un **CString** miembro de datos.|
|[DDX_OCTextRO](#ddx_octextro)|Administra la transferencia de **CString** datos entre una propiedad de solo lectura de un control OLE y un **CString** miembro de datos.|

##  <a name="ddx_ocbool"></a>  DDX_OCBool

El `DDX_OCBool` administra la transferencia de la función **BOOL** datos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **BOOL** miembro de datos del cuadro de diálogo, vista de formulario, o objeto de vista del control.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado:** afxdisp.h

##  <a name="ddx_ocboolro"></a>  DDX_OCBoolRO

El `DDX_OCBoolRO` administra la transferencia de la función **BOOL** datos entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **BOOL** miembro de datos del cuadro de diálogo vista de formulario, o el objeto de vista de control.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_occolor"></a>  DDX_OCColor

El `DDX_OCColor` función administra la transferencia de datos OLE_COLOR entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario, o el objeto de vista de control y un miembro de datos OLE_COLOR del cuadro de diálogo, vista de formulario, o controlar el objeto de vista.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_occolorro"></a>  DDX_OCColorRO

El `DDX_OCColorRO` función administra la transferencia de datos OLE_COLOR entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario, o el objeto de vista de control y un miembro de datos OLE_COLOR del cuadro de diálogo, vista de formulario, o controlar el objeto de vista.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_ocfloat"></a>  DDX_OCFloat

El `DDX_OCFloat` administra la transferencia de la función **float** (o **doble**) datos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **float** (o **doble**) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_ocfloatro"></a>  DDX_OCFloatRO

El `DDX_OCFloatRO` administra la transferencia de la función **float** (o **doble**) datos entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un  **float** (o **doble**) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_ocint"></a>  DDX_OCInt

El `DDX_OCInt` administra la transferencia de la función **int** (o **largo**) datos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **int**(o **largo**) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_ocintro"></a>  DDX_OCIntRO

El `DDX_OCIntRO` administra la transferencia de la función **int** (o **largo**) datos entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **int** (o **largo**) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_ocshort"></a>  DDX_OCShort

El `DDX_OCShort` función administra la transferencia de datos cortos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario, o el objeto de vista de control y un miembro de datos cortos del cuadro de diálogo, vista de formulario, o controlar el objeto de vista.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_ocshortro"></a>  DDX_OCShortRO

El `DDX_OCShortRO` función administra la transferencia de datos cortos entre una propiedad de solo lectura de un control OLE en un cuadro de diálogo, vista de formulario, o el objeto de vista de control y un miembro de datos cortos del cuadro de diálogo, vista de formulario, o controlar el objeto de vista.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_octext"></a>  DDX_OCText

El **DDX_OCText** administra la transferencia de la función **CString** datos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **CString** datos miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="ddx_octextro"></a>  DDX_OCTextRO

La función `DDX_OCTextRO` administra la transferencia de datos `CString` entre una propiedad de solo lectura de un control OLE de un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos `CString` del objeto de cuadro de dialogo, vista de formulario o vista de control.

```
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

*DISPID*<br/>
Identificador de envío de una propiedad del control.

*valor*<br/>
Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
