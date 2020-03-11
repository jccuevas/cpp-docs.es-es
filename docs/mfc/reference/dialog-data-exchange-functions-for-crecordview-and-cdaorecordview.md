---
title: Funciones de intercambio de datos de cuadro de diálogo para CRecordView y CDaoRecordView
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 8b216941837cd79492aa6cb707481073b5321bce
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866599"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funciones de intercambio de datos de cuadro de diálogo para CRecordView y CDaoRecordView

En este tema se enumeran las funciones de DDX_Field que se usan para intercambiar datos entre un formulario [CRecordset](../../mfc/reference/crecordset-class.md) y [CRecordView](../../mfc/reference/crecordview-class.md) , o un formulario [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) . DAO se utiliza con bases de datos de Access y se admite a través de Office 2013. DAO 3,6 es la versión final y se considera obsoleta.

> [!NOTE]
>  DDX_Field funciones son similares a las funciones DDX en que intercambian datos con controles en un formulario. Pero a diferencia de DDX, intercambian datos con los campos del objeto de conjunto de registros asociado de la vista, en lugar de con los campos de la propia vista de registros. Para obtener más información, vea clases `CRecordView` y `CDaoRecordView`.

### <a name="ddx_field-functions"></a>Funciones de DDX_Field

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Transfiere datos enteros entre un miembro de datos de un campo de conjunto de registros y el índice de la selección actual en un cuadro combinado en [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Transfiere datos de `CString` entre un miembro de datos de un campo de conjunto de registros y el control de edición de un cuadro combinado en un `CRecordView` o `CDaoRecordView`. Al mover los datos del conjunto de registros al control, esta función selecciona el elemento en el cuadro combinado que comienza con los caracteres de la cadena especificada.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Transfiere datos de `CString` entre un miembro de datos de un campo de conjunto de registros y el control de edición de un cuadro combinado en un `CRecordView` o `CDaoRecordView`. Al mover los datos del conjunto de registros al control, esta función selecciona el elemento en el cuadro combinado que coincide exactamente con la cadena especificada.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Transfiere datos booleanos entre un miembro de datos de un campo de conjunto de registros y una casilla en un `CRecordView` o `CDaoRecordView`.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Transfiere datos enteros entre un miembro de datos de un campo de conjunto de registros y el índice de la selección actual en un cuadro de lista en un `CRecordView` o `CDaoRecordView`.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Administra la transferencia de datos [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros. Al mover los datos del conjunto de registros al control, esta función selecciona el elemento en el cuadro de lista que comienza con los caracteres de la cadena especificada.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Administra la transferencia de datos de `CString` entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros. Cuando se mueven datos del conjunto de registros al control, esta función selecciona el primer elemento que coincide exactamente con la cadena especificada.|
|[DDX_FieldRadio](#ddx_fieldradio)|Transfiere datos enteros entre un miembro de datos de un campo de conjunto de registros y un grupo de botones de radio de un `CRecordView` o `CDaoRecordView`.|
|[DDX_FieldScroll](#ddx_fieldscroll)|Establece u obtiene la posición de desplazamiento de un control de barra de desplazamiento en un `CRecordView` o `CDaoRecordView`. Llame a desde la función [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) .|
|[DDX_FieldSlider](#ddx_fieldslider)|Sincroniza la posición Thumb de un control deslizante en una vista de registros y un miembro de datos de campo `int` de un conjunto de registros. |
|[DDX_FieldText](#ddx_fieldtext)|Hay disponibles versiones sobrecargadas para transferir los datos `int`, **uint**, **Long**, `DWORD`[, CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **Double**, **Short**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)y [COleCurrency](../../mfc/reference/colecurrency-class.md) entre un miembro de datos de un campo de conjunto de registros y un cuadro de edición en un `CRecordView` o `CDaoRecordView`.|

##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex

La función `DDX_FieldCBIndex` sincroniza el índice del elemento seleccionado en el control de cuadro de lista de un control de cuadro combinado en una vista de registros y un miembro de datos de campo `int` de un conjunto de registros asociado a la vista de registros.

```
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de un control en el objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*índice*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Cuando se mueven datos del conjunto de registros al control, esta función establece la selección en el control basándose en el valor especificado en *index*. En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es null, MFC establece el valor del índice en 0. En una transferencia desde el control al conjunto de registros, si el control está vacío o si no hay ningún elemento seleccionado, el campo de conjunto de registros se establece en 0.

Use la primera versión si está trabajando con las clases basadas en ODBC. Use la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. El ejemplo sería similar para `DDX_FieldCBIndex`.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString

La función `DDX_FieldCBString` administra la transferencia de datos [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre el control de edición de un control de cuadro combinado en una vista de registros y un miembro de datos de campo `CString` de un conjunto de registros asociado a la vista de registros.

```
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de un control en el objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Cuando se mueven datos del conjunto de registros al control, esta función establece la selección actual del cuadro combinado en la primera fila que comienza con los caracteres de la cadena especificada en *valor*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es null, se quita cualquier selección del cuadro combinado y el control de edición del cuadro combinado se establece en Empty. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en NULL si el campo lo permite.

Use la primera versión si está trabajando con las clases basadas en ODBC. Use la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. En el ejemplo se incluye una llamada a `DDX_FieldCBString`.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact

La función `DDX_FieldCBStringExact` administra la transferencia de datos [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre el control de edición de un control de cuadro combinado en una vista de registros y un miembro de datos de campo `CString` de un conjunto de registros asociado a la vista de registros.

```
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de un control en el objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Cuando se mueven datos del conjunto de registros al control, esta función establece la selección actual del cuadro combinado en la primera fila que coincide exactamente con la cadena especificada en *valor*. En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es NULL, se quita cualquier selección del cuadro combinado y el cuadro de edición del cuadro combinado se establece en vacío. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en NULL.

Use la primera versión si está trabajando con las clases basadas en ODBC. Use la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldCBStringExact` serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

##  <a name="ddx_fieldcheck"></a>  DDX_FieldCheck

La función `DDX_FieldCheck` administra la transferencia de datos **int** entre un control de casilla en un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos **int** del objeto de cuadro de diálogo, vista de formulario o vista de control.

```
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control de casilla asociado a la propiedad de control.

*value*<br/>
Referencia a una variable miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Cuando se llama a `DDX_FieldCheck`, el *valor* se establece en el estado actual del control de casilla, o el estado del control se establece en *valor*, dependiendo de la dirección de la transferencia.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

##  <a name="ddx_fieldlbindex"></a>  DDX_FieldLBIndex

La función `DDX_FieldLBIndex` sincroniza el índice del elemento seleccionado en un control de cuadro de lista en una vista de registros y un miembro de datos de campo **int** de un conjunto de registros asociado a la vista de registros.

```
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de un control en el objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*índice*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Cuando se mueven datos del conjunto de registros al control, esta función establece la selección en el control basándose en el valor especificado en *index*. En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es null, MFC establece el valor del índice en 0. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en 0.

Use la primera versión si está trabajando con las clases basadas en ODBC. Use la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

##  <a name="ddx_fieldlbstring"></a>  DDX_FieldLBString

`DDX_FieldLBString` copia la selección actual de un control de cuadro de lista en una vista de registros en un miembro de datos de campo [CString](../../atl-mfc-shared/reference/cstringt-class.md) de un conjunto de registros asociado a la vista de registros.

```
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de un control en el objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

En la dirección inversa, esta función establece la selección actual del cuadro de lista en la primera fila que comienza con los caracteres de la cadena especificada por *valor*. En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es null, se quita cualquier selección del cuadro de lista. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en NULL.

Use la primera versión si está trabajando con las clases basadas en ODBC. Use la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldLBString` serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

##  <a name="ddx_fieldlbstringexact"></a>  DDX_FieldLBStringExact

La función `DDX_FieldLBStringExact` copia la selección actual de un control de cuadro de lista en una vista de registros en un miembro de datos de campo [CString](../../atl-mfc-shared/reference/cstringt-class.md) de un conjunto de registros asociado a la vista de registros.

```
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de un control en el objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

En la dirección inversa, esta función establece la selección actual del cuadro de lista en la primera fila que coincide exactamente con la cadena especificada en *valor*. En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es null, se quita cualquier selección del cuadro de lista. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en NULL.

Use la primera versión si está trabajando con las clases basadas en ODBC. Use la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldLBStringExact` serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

##  <a name="ddx_fieldradio"></a>  DDX_FieldRadio

La función `DDX_FieldRadio` asocia una variable miembro **int** de base cero del conjunto de registros de una vista de registros con el botón de radio seleccionado actualmente en un grupo de botones de radio de la vista de registros.

```
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR del primer de un grupo (con el estilo WS_GROUP) de los controles de botón de radio adyacentes del objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Al transferir desde el campo de conjunto de registros a la vista, esta función activa el botón de radio *nth* (basado en cero) y desactiva los demás botones. En la dirección inversa, esta función establece el campo de conjunto de registros en el número ordinal del botón de radio que se encuentra actualmente en (activada). En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es null, no se selecciona ningún botón. En una transferencia desde el control al conjunto de registros, si no hay ningún control seleccionado, el campo de conjunto de registros se establece en NULL si el campo lo permite.

Use la primera versión si está trabajando con las clases basadas en ODBC. Use la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldRadio` serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll

La función `DDX_FieldScroll` sincroniza la posición de desplazamiento de un control de barra de desplazamiento en una vista de registros y un miembro de datos de campo **int** de un conjunto de registros asociado a la vista de registros (o con cualquier variable de entero que elija para asignarlo).

```
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR del primer de un grupo (con el estilo WS_GROUP) de los controles de botón de radio adyacentes del objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Cuando se mueven datos del conjunto de registros al control, esta función establece la posición de desplazamiento del control de barra de desplazamiento en el valor especificado en *valor*. En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es null, el control de barra de desplazamiento se establece en 0. En una transferencia desde el control al conjunto de registros, si el control está vacío, el valor del campo de conjunto de registros es 0.

Use la primera versión si está trabajando con las clases basadas en ODBC. Use la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldScroll` serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

  ## <a name="ddx_fieldslider"></a>  DDX_FieldSlider
La función `DDX_FieldSlider` sincroniza la posición Thumb de un control deslizante en una vista de registros y un miembro de datos de campo **int** de un conjunto de registros asociado a la vista de registros (o con cualquier variable de entero que elija para asignarlo).

### <a name="syntax"></a>Sintaxis

  ```
   void AFXAPI DDX_FieldSlider(
       CDataExchange* pDX,
       int nIDC,
       int& value,
       CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de recurso del control deslizante.

*value*<br/>
Referencia al valor que se va a intercambiar. Este parámetro contiene o se utilizará para establecer la posición de colocación actual del control deslizante.

*pRecordset*<br/>
Puntero al `CRecordset` asociado o `CDaoRecordset` objeto con el que se intercambian los datos.

### <a name="remarks"></a>Observaciones

Cuando se mueven datos del conjunto de registros al control deslizante, esta función establece la posición del control deslizante en el valor especificado en *valor*. En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es null, la posición del control deslizante se establece en 0. En una transferencia del control al conjunto de registros, si el control está vacío, el valor del campo de conjunto de registros es 0.

`DDX_FieldSlider` no intercambia información de intervalo con controles deslizantes capaces de establecer un intervalo en lugar de simplemente una posición.

Utilice la primera invalidación de la función si está trabajando con las clases basadas en ODBC. Use la segunda invalidación con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para `CRecordView` y `CDaoRecordView` campos, vea [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener información acerca de los controles deslizantes, vea [usar CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldSlider` serían similares.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

##  <a name="ddx_fieldtext"></a>  DDX_FieldText

La función `DDX_FieldText` administra la transferencia de **datos int**, **Short**, **Long**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **Double**, **bool**o **byte** entre un control de cuadro de edición y los miembros de datos de campo de un conjunto de registros.

```
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
IDENTIFICADOR de un control en el objeto [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Referencia a un miembro de datos de campo en el `CRecordset` asociado o `CDaoRecordset` objeto. El tipo de datos del valor depende de cuál de las versiones sobrecargadas de `DDX_FieldText` utilice.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos. Este puntero permite a `DDX_FieldText` detectar y establecer valores NULL.

### <a name="remarks"></a>Observaciones

En el caso de los objetos [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), `DDX_FieldText` también administra la transferencia de los valores [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) y [COleCurrency](../../mfc/reference/colecurrency-class.md). Un control de cuadro de edición vacío indica un valor nulo. En una transferencia del conjunto de registros al control, si el campo del conjunto de registros es null, el cuadro de edición se establece en Empty. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en NULL.

Use las versiones con parámetros de [CRecordset](../../mfc/reference/crecordset-class.md) si está trabajando con las clases basadas en ODBC. Use las versiones con parámetros [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) si está trabajando con las clases basadas en Dao.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

La siguiente función de `DoDataExchange` para un [CRecordView](../../mfc/reference/crecordview-class.md) contiene `DDX_FieldText` llamadas de función para tres tipos de datos: `IDC_COURSELIST` es un cuadro combinado. los otros dos controles son cuadros de edición. En la programación DAO, el parámetro *m_pSet* es un puntero a una [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)
