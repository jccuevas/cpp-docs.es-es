---
title: Rutinas de validación de datos de cuadros de diálogo estándar
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: dce982f76e25da424c02d621c1b760ec29e88918
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850169"
---
# <a name="standard-dialog-data-validation-routines"></a>Rutinas de validación de datos de cuadros de diálogo estándar

En este tema se enumera las rutinas de validación (DDV) de datos de cuadro de diálogo estándar utilizadas para los controles de cuadro de diálogo comunes de MFC.

> [!NOTE]
>  Las rutinas de intercambio de datos de cuadro de diálogo estándar se definen en el afxdd_.h del archivo de encabezado. Sin embargo, las aplicaciones deben incluir afxwin.h.

### <a name="ddv-functions"></a>Funciones DDV

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Comprueba que el número de caracteres en un valor de un control determinado no superar un máximo especificado.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Comprueba un valor de control determinada no supera un determinado **bytes** intervalo.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Comprueba el que valor de un control determinado no supera un intervalo de tiempo determinado.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Comprueba un valor de control determinada no supera un determinado **doble** intervalo.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Comprueba un valor de control determinada no supera un determinado **DWORD** intervalo.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Comprueba un valor de control determinada no supera un determinado **float** intervalo.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Comprueba un valor de control determinada no supera un determinado **int** intervalo.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Comprueba un valor de control determinada no supera un determinado **largo** intervalo.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Comprueba un valor de control determinada no supera un determinado **LONGLONG** intervalo.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Comprueba el que valor de un control determinado no supera un intervalo de fechas determinado.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Comprueba un valor de control determinada no supera un determinado **corto** intervalo.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Comprueba que el valor de un control deslizante determinado se encuentra dentro del intervalo especificado.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Comprueba un valor de control determinada no supera un determinado **UINT** intervalo.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Comprueba el que valor de un control determinado se encuentra entre dos valores especificados.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Comprueba un valor de control determinada no supera un determinado **ULONGLONG** intervalo.|

##  <a name="ddv_maxchars"></a>  DDV_MaxChars

Llame a `DDV_MaxChars` para comprobar que la cantidad de caracteres en el control asociado *valor* no supere los *nChars*.

```
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*value*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*nChars*<br/>
Número máximo de caracteres permitidos.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxbyte"></a>  DDV_MinMaxByte

Llame a `DDV_MinMaxByte` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo bytes) permitido.

*maxVal*<br/>
Valor máximo (de tipo bytes) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxdatetime"></a>  DDV_MinMaxDateTime

Llame a `DDV_MinMaxDateTime` para comprobar que el valor de fecha y hora en el selector de fecha y hora control ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) asociado con *refValue* se encuentra entre *refMinRange*y *refMaxRange*.

```
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
Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) o [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto asociado a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control. Este objeto contiene los datos que se va a validarse.

*refMinRange*<br/>
Mínimo valor permitido de fecha y hora.

*refMaxRange*<br/>
Valor de fecha y hora máximo permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxdouble"></a>  DDV_MinMaxDouble

Llame a `DDV_MinMaxDouble` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo **doble**) permitido.

*maxVal*<br/>
Valor máximo (de tipo **doble**) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxdword"></a>  DDV_MinMaxDWord

Llame a `DDV_MinMaxDWord` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo DWORD) permitido.

*maxVal*<br/>
Valor máximo (de tipo DWORD) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxfloat"></a>  DDV_MinMaxFloat

Llame a `DDV_MinMaxFloat` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo **float**) permitido.

*maxVal*<br/>
Valor máximo (de tipo **float**) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxint"></a>  DDV_MinMaxInt

Llame a `DDV_MinMaxInt` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo **int**) permitido.

*maxVal*<br/>
Valor máximo (de tipo **int**) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxlong"></a>  DDV_MinMaxLong

Llame a `DDV_MinMaxLong` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo **largo**) permitido.

*maxVal*<br/>
Valor máximo (de tipo **largo**) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxlonglong"></a>  DDV_MinMaxLongLong

Llame a `DDV_MinMaxLongLong` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo LONGLONG) permitido.

*maxVal*<br/>
Valor máximo (de tipo LONGLONG) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxmonth"></a>  DDV_MinMaxMonth

Llame a `DDV_MinMaxMonth` para comprobar que el valor de fecha y hora en el calendario mensual control ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) asociado con *refValue* se encuentra entre *refMinRange* y *refMaxRange*.

```
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
Una referencia a un objeto de tipo `CTime` o `COleDateTime` asociado a una variable de miembro del cuadro de diálogo, vista de formulario o controlar el objeto de vista. Este objeto contiene los datos que se va a validarse. Pasadas MFC esta referencia cuando `DDV_MinMaxMonth` se llama.

*refMinRange*<br/>
Mínimo valor permitido de fecha y hora.

*refMaxRange*<br/>
Valor de fecha y hora máximo permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxshort"></a>  DDV_MinMaxShort

Llame a `DDV_MinMaxShort` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo **corto**) permitido.

*maxVal*<br/>
Valor máximo (de tipo **corto**) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxslider"></a>  DDV_MinMaxSlider

Llame a `DDV_MinMaxSlider` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia al valor que se va a validar. Este parámetro contiene o establece la posición de control de posición actual del control deslizante.

*minVal*<br/>
Valor mínimo permitido.

*maxVal*<br/>
Valor máximo permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md). Para obtener información acerca de los controles deslizantes, consulte [usar CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxuint"></a>  DDV_MinMaxUInt

Llame a `DDV_MinMaxUInt` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo UINT) permitido.

*maxVal*<br/>
Valor máximo (de tipo UINT) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

##  <a name="ddv_minmaxulonglong"></a>  DDV_MinMaxULongLong

Llame a `DDV_MinMaxULongLong` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo ULONGLONG) permitido.

*maxVal*<br/>
Valor máximo (de tipo ULONGLONG) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdd_.h

## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned

Llame a `DDV_MinMaxUnsigned` para comprobar que el valor en el control asociado *valor* se encuentra entre *propiedades minVal* y *maxVal*.

### <a name="syntax"></a>Sintaxis

```
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
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se validan los datos de objeto de vista de control.

*minVal*<br/>
Valor mínimo (de tipo **sin signo** ) permitido.

*maxVal*<br/>
Valor máximo (de tipo **sin signo** ) permitido.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de DDV, vea [intercambio de datos de cuadro de diálogo y validación](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdd_.h

## <a name="see-also"></a>Vea también

[Rutinas de intercambio de datos de cuadros de diálogo estándar](standard-dialog-data-exchange-routines.md)<br/>
[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)

