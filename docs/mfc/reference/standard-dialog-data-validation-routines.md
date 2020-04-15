---
title: Rutinas de validación de datos de cuadros de diálogo estándar
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 83e3e215ec8d66321bbac5a4a308b04ef69dc68c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372897"
---
# <a name="standard-dialog-data-validation-routines"></a>Rutinas de validación de datos de cuadros de diálogo estándar

En este tema se enumeran las rutinas de validación de datos de cuadro de diálogo estándar (DDV) utilizadas para los controles de cuadro de diálogo MFC comunes.

> [!NOTE]
> Las rutinas de intercambio de datos de cuadro de diálogo estándar se definen en el archivo de cabecera afxdd_.h. Sin embargo, las aplicaciones deben incluir afxwin.h.

### <a name="ddv-functions"></a>Funciones DDV

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Comprueba que el número de caracteres de un valor de control determinado no supere un máximo determinado.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Comprueba que un valor de control determinado no supere un intervalo **BYTE** determinado.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Comprueba que un valor de control determinado no supere un intervalo de tiempo determinado.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Comprueba que un valor de control determinado no supere un **intervalo doble** determinado.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Comprueba que un valor de control determinado no supere un intervalo **DWORD** determinado.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Comprueba que un valor de control determinado no supere un intervalo **de float** determinado.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Comprueba que un valor de control determinado no supere un intervalo **int** determinado.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Comprueba que un valor de control determinado no supere un intervalo **largo** determinado.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Comprueba que un valor de control determinado no supere un intervalo **LONGLONG** determinado.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Comprueba que un valor de control determinado no supere un intervalo de fechas determinado.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Comprueba que un valor de control determinado no supere un intervalo **corto** determinado.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Comprueba que un valor de control de control deslizante determinado se encuentre dentro del intervalo especificado.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Comprueba que un valor de control determinado no supere un intervalo **UINT** determinado.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Comprueba que un valor de control determinado se encuentra entre dos valores especificados.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Comprueba que un valor de control determinado no supere un intervalo **ULONGLONG** determinado.|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

Llame `DDV_MaxChars` para comprobar que la cantidad de caracteres en el control asociado con *value* no supera *nChars*.

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*nChars*<br/>
Número máximo de caracteres permitidos.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

Llame `DDV_MinMaxByte` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Valor mínimo (de tipo BYTE) permitido.

*maxVal*<br/>
Valor máximo (de tipo BYTE) permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

Llame `DDV_MinMaxDateTime` para comprobar que el valor de fecha y hora en el control de selector de fecha y hora ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) asociado a *refValue* se encuentra entre *refMinRange* y *refMaxRange*.

```cpp
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar este objeto.

*refValue*<br/>
Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) o [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto asociado a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control. Este objeto contiene los datos que se van a validar.

*refMinRange*<br/>
Valor mínimo de fecha y hora permitido.

*refMaxRange*<br/>
Valor máximo de fecha y hora permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

Llame `DDV_MinMaxDouble` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Se permite el valor mínimo (de tipo **double ).**

*maxVal*<br/>
Se permite el valor máximo (de tipo **double ).**

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

Llame `DDV_MinMaxDWord` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Valor mínimo (de tipo DWORD) permitido.

*maxVal*<br/>
Valor máximo (de tipo DWORD) permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

Llame `DDV_MinMaxFloat` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Se permite el valor mínimo (de tipo **float ).**

*maxVal*<br/>
Se permite el valor máximo (de tipo **float ).**

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

Llame `DDV_MinMaxInt` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Valor mínimo (de tipo **int**) permitido.

*maxVal*<br/>
Valor máximo (de tipo **int**) permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

Llame `DDV_MinMaxLong` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Se permite el valor mínimo (de tipo **long**).

*maxVal*<br/>
Se permite el valor máximo (de tipo **long**).

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

Llame `DDV_MinMaxLongLong` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Valor mínimo (de tipo LONGLONG) permitido.

*maxVal*<br/>
Valor máximo (de tipo LONGLONG) permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

Llame `DDV_MinMaxMonth` para comprobar que el valor de hora y fecha en el control de calendario de mes ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) asociado a *refValue* se encuentra entre *refMinRange* y *refMaxRange*.

```cpp
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*refValue*<br/>
Una referencia a un `CTime` `COleDateTime` objeto de tipo o asociado a una variable miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control. Este objeto contiene los datos que se van a validar. MFC pasa esta `DDV_MinMaxMonth` referencia cuando se llama.

*refMinRange*<br/>
Valor mínimo de fecha y hora permitido.

*refMaxRange*<br/>
Valor máximo de fecha y hora permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

Llame `DDV_MinMaxShort` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Valor mínimo (de tipo **short**) permitido.

*maxVal*<br/>
Valor máximo (de tipo **short**) permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

Llame `DDV_MinMaxSlider` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia al valor que se va a validar. Este parámetro mantiene o establece la posición actual del pulgar del control deslizante.

*minVal*<br/>
Valor mínimo permitido.

*maxVal*<br/>
Valor máximo permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Para obtener información acerca de los controles deslizantes, consulte Uso de [CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

Llame `DDV_MinMaxUInt` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Valor mínimo (de tipo UINT) permitido.

*maxVal*<br/>
Valor máximo (de tipo UINT) permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

Llame `DDV_MinMaxULongLong` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Valor mínimo (de tipo ULONGLONG) permitido.

*maxVal*<br/>
Valor máximo (de tipo ULONGLONG) permitido.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

Llame `DDV_MinMaxUnsigned` para comprobar que el valor del control asociado al *valor* se encuentra entre *minVal* y *maxVal*.

### <a name="syntax"></a>Sintaxis

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se validan los datos.

*minVal*<br/>
Se permite el valor mínimo (de tipo **unsigned** ).

*maxVal*<br/>
Se permite el valor máximo (de tipo **unsigned** ).

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de DDV, vea [Dialog Data Exchange and Validation](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdd_.h

## <a name="see-also"></a>Consulte también

[Rutinas de intercambio de datos de cuadros de diálogo estándar](standard-dialog-data-exchange-routines.md)<br/>
[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
