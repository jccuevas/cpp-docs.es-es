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
ms.openlocfilehash: 3128b1ba459cb017d1cdb2321bc55d865aa4f8b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365773"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funciones de intercambio de datos de cuadro de diálogo para CRecordView y CDaoRecordView

En este tema se enumeran las funciones DDX_Field utilizadas para intercambiar datos entre un [CRecordset](../../mfc/reference/crecordset-class.md) y un [Formulario CRecordView](../../mfc/reference/crecordview-class.md) o un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) y un [formulario CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) DAO se usa con bases de datos de Access y se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto.

> [!NOTE]
> DDX_Field funciones son como funciones DDX en que intercambian datos con controles en un formulario. Pero a diferencia de DDX, intercambian datos con los campos del objeto de conjunto de registros asociado de la vista en lugar de con los campos de la propia vista de registro. Para obtener más `CRecordView` información, consulte clases y `CDaoRecordView`.

### <a name="ddx_field-functions"></a>Funciones DDX_Field

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Transfiere datos enteros entre un miembro de datos de campo de conjunto de registros y el índice de la selección actual en un cuadro combinado en un [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Transfiere `CString` datos entre un miembro de datos de campo `CRecordView` de `CDaoRecordView`conjunto de registros y el control de edición de un cuadro combinado en un o . Al mover datos del conjunto de registros al control, esta función selecciona el elemento en el cuadro combinado que comienza con los caracteres de la cadena especificada.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Transfiere `CString` datos entre un miembro de datos de campo `CRecordView` de `CDaoRecordView`conjunto de registros y el control de edición de un cuadro combinado en un o . Al mover datos del conjunto de registros al control, esta función selecciona el elemento en el cuadro combinado que coincide exactamente con la cadena especificada.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Transfiere datos booleanos entre un miembro de `CRecordView` `CDaoRecordView`datos de campo de conjunto de registros y una casilla de verificación en un o .|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Transfiere datos enteros entre un miembro de datos de campo de `CRecordView` conjunto `CDaoRecordView`de registros y el índice de la selección actual en un cuadro de lista en un o .|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Administra la transferencia de datos [de CString](../../atl-mfc-shared/reference/cstringt-class.md) entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros. Al mover datos del conjunto de registros al control, esta función selecciona el elemento en el cuadro de lista que comienza con los caracteres de la cadena especificada.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Administra la `CString` transferencia de datos entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros. Al mover datos del conjunto de registros al control, esta función selecciona el primer elemento que coincide exactamente con la cadena especificada.|
|[DDX_FieldRadio](#ddx_fieldradio)|Transfiere datos enteros entre un miembro de datos de `CRecordView` `CDaoRecordView`campo de conjunto de registros y un grupo de botones de opción en un o .|
|[DDX_FieldScroll](#ddx_fieldscroll)|Establece u obtiene la posición de desplazamiento `CRecordView` de `CDaoRecordView`un control de barra de desplazamiento en un o . Llamada desde la función [DoFieldExchange.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)|
|[DDX_FieldSlider](#ddx_fieldslider)|Sincroniza la posición del control deslizante de un `int` control deslizante en una vista de registro y un miembro de datos de campo de un conjunto de registros. |
|[DDX_FieldText](#ddx_fieldtext)|Las versiones sobrecargadas `int`están disponibles para `DWORD`transferir datos , **UINT**, **long**, , [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **short** `CDaoRecordView`, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)y [COleCurrency](../../mfc/reference/colecurrency-class.md) entre un miembro de datos de campo de conjunto de registros y un cuadro de edición en un `CRecordView` o .|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

La `DDX_FieldCBIndex` función sincroniza el índice del elemento seleccionado en el control de cuadro `int` de lista de un control de cuadro combinado en una vista de registroy un miembro de datos de campo de un conjunto de registros asociado a la vista de registros.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*índice*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Al mover datos del conjunto de registros al control, esta función establece la selección en el control en función del valor especificado en *index*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, MFC establece el valor del índice en 0. En una transferencia de control a conjunto de registros, si el control está vacío o si no se selecciona ningún elemento, el campo de conjunto de registros se establece en 0.

Utilice la primera versión si está trabajando con las clases basadas en ODBC. Utilice la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. El ejemplo sería `DDX_FieldCBIndex`similar para .

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString

La `DDX_FieldCBString` función administra la transferencia de datos [de CString](../../atl-mfc-shared/reference/cstringt-class.md) entre el `CString` control de edición de un control de cuadro combinado en una vista de registro y un miembro de datos de campo de un conjunto de registros asociado a la vista de registros.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Al mover datos del conjunto de registros al control, esta función establece la selección actual en el cuadro combinado en la primera fila que comienza con los caracteres de la cadena especificada en *value*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, cualquier selección se quita del cuadro combinado y el control de edición del cuadro combinado se establece en vacío. En una transferencia de control a conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null si el campo lo permite.

Utilice la primera versión si está trabajando con las clases basadas en ODBC. Utilice la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. El ejemplo incluye `DDX_FieldCBString`una llamada a .

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

La `DDX_FieldCBStringExact` función administra la transferencia de datos [de CString](../../atl-mfc-shared/reference/cstringt-class.md) entre el `CString` control de edición de un control de cuadro combinado en una vista de registro y un miembro de datos de campo de un conjunto de registros asociado a la vista de registros.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Al mover datos del conjunto de registros al control, esta función establece la selección actual en el cuadro combinado en la primera fila que coincide exactamente con la cadena especificada en *value*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es NULL, cualquier selección se quita del cuadro combinado y el cuadro de edición del cuadro combinado se establece en vacío. En una transferencia de control a conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en NULL.

Utilice la primera versión si está trabajando con las clases basadas en ODBC. Utilice la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las `DDX_FieldCBStringExact` llamadas serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck

La `DDX_FieldCheck` función administra la transferencia de datos **int** entre un control de casilla de verificación en un cuadro de diálogo, vista de formulario o objeto de vista de control y un miembro de datos **int** del cuadro de diálogo, vista de formulario o objeto de vista de control.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de casilla de verificación asociado a la propiedad de control.

*value*<br/>
Una referencia a una variable miembro del cuadro de diálogo, vista de formulario o objeto de vista de control con el que se intercambian datos.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Cuando `DDX_FieldCheck` se llama, *value* se establece en el estado actual del control de casilla de verificación o el estado del control se establece en *value*, dependiendo de la dirección de transferencia.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

La `DDX_FieldLBIndex` función sincroniza el índice del elemento seleccionado en un control de cuadro de lista en una vista de registro y un miembro de datos de campo **int** de un conjunto de registros asociado a la vista de registros.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*índice*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Al mover datos del conjunto de registros al control, esta función establece la selección en el control en función del valor especificado en *index*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, MFC establece el valor del índice en 0. En una transferencia de control a conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en 0.

Utilice la primera versión si está trabajando con las clases basadas en ODBC. Utilice la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString

`DDX_FieldLBString` copia la selección actual de un control de cuadro de lista en una vista de registros en un miembro de datos de campo [CString](../../atl-mfc-shared/reference/cstringt-class.md) de un conjunto de registros asociado a la vista de registros.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

En la dirección inversa, esta función establece la selección actual en el cuadro de lista en la primera fila que comienza con los caracteres de la cadena especificada por *value*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, cualquier selección se quita del cuadro de lista. En una transferencia de control a conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.

Utilice la primera versión si está trabajando con las clases basadas en ODBC. Utilice la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las `DDX_FieldLBString` llamadas serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

La `DDX_FieldLBStringExact` función copia la selección actual de un control de cuadro de lista en una vista de registro a un miembro de datos de campo [CString](../../atl-mfc-shared/reference/cstringt-class.md) de un conjunto de registros asociado a la vista de registros.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

En la dirección inversa, esta función establece la selección actual en el cuadro de lista en la primera fila que coincide exactamente con la cadena especificada en *value*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, cualquier selección se quita del cuadro de lista. En una transferencia de control a conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.

Utilice la primera versión si está trabajando con las clases basadas en ODBC. Utilice la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las `DDX_FieldLBStringExact` llamadas serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio

La `DDX_FieldRadio` función asocia una variable miembro **int** de base cero del conjunto de registros de una vista de registro con el botón de opción seleccionado actualmente en un grupo de botones de opción en la vista de registros.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador del primero en un grupo (con estilo WS_GROUP) de controles de botón de opción adyacentes en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Al transferir desde el campo de conjunto de registros a la vista, esta función activa el *enésimo* botón de opción (basado en cero) y desactiva los otros botones. En la dirección inversa, esta función establece el campo de conjunto de registros en el número ordinal del botón de opción que está actualmente activado (marcado). En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, no se selecciona ningún botón. En una transferencia de control a conjunto de registros, si no se selecciona ningún control, el campo de conjunto de registros se establece en Null si el campo lo permite.

Utilice la primera versión si está trabajando con las clases basadas en ODBC. Utilice la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las `DDX_FieldRadio` llamadas serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll

La `DDX_FieldScroll` función sincroniza la posición de desplazamiento de un control de barra de desplazamiento en una vista de registro y un miembro de datos de campo **int** de un conjunto de registros asociado a la vista de registros (o con cualquier variable de entero a la que elija asignarlo).

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador del primero en un grupo (con estilo WS_GROUP) de controles de botón de opción adyacentes en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Al mover datos del conjunto de registros al control, esta función establece la posición de desplazamiento del control de barra de desplazamiento en el valor especificado en *value*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, el control de barra de desplazamiento se establece en 0. En una transferencia de control a conjunto de registros, si el control está vacío, el valor del campo de conjunto de registros es 0.

Utilice la primera versión si está trabajando con las clases basadas en ODBC. Utilice la segunda versión si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las `DDX_FieldScroll` llamadas serían similares.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a>DDX_FieldSlider

La `DDX_FieldSlider` función sincroniza la posición del pulgar de un control deslizante en una vista de registro y un miembro de datos de campo **int** de un conjunto de registros asociado a la vista de registros (o con cualquier variable de entero a la que elija asignarlo).

### <a name="syntax"></a>Sintaxis

```cpp
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
Un puntero a un [CDataExchange](cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control deslizante.

*value*<br/>
Una referencia al valor que se va a intercambiar. Este parámetro se mantiene o se utilizará para establecer la posición actual del pulgar del control deslizante.

*pRecordset*<br/>
Puntero al objeto `CRecordset` `CDaoRecordset` u objeto asociado con el que se intercambian datos.

### <a name="remarks"></a>Observaciones

Al mover datos del conjunto de registros al control deslizante, esta función establece la posición del control deslizante en el valor especificado en *value*. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, la posición del control deslizante se establece en 0. En una transferencia del control al conjunto de registros, si el control está vacío, el valor del campo de conjunto de registros es 0.

`DDX_FieldSlider`no intercambia información de rango con controles deslizantes capaces de establecer un rango en lugar de simplemente una posición.

Utilice la primera invalidación de la función si está trabajando con las clases basadas en ODBC. Utilice la segunda invalidación con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../dialog-data-exchange-and-validation.md). Para obtener ejemplos y más `CRecordView` `CDaoRecordView` información sobre DDX para y campos, vea Vistas de [registros](../../data/record-views-mfc-data-access.md). Para obtener información acerca de los controles deslizantes, consulte Uso de [CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las `DDX_FieldSlider` llamadas serían similares.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText

La `DDX_FieldText` función administra la transferencia de datos **int**, **short**, **long**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **BOOL**o **BYTE** entre un control de cuadro de edición y los miembros de datos de campo de un conjunto de registros.

```cpp
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
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro `CRecordset` de `CDaoRecordset` datos de campo en el objeto u asociado. El tipo de datos de valor depende `DDX_FieldText` de cuál de las versiones sobrecargadas de uso.

*pRecordset*<br/>
Puntero al objeto [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian datos. Este puntero `DDX_FieldText` permite detectar y establecer valores Null.

### <a name="remarks"></a>Observaciones

En el caso de los objetos [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), `DDX_FieldText` también administra la transferencia de los valores [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) y [COleCurrency](../../mfc/reference/colecurrency-class.md). Un control de cuadro de edición vacío indica un valor Null. En una transferencia del conjunto de registros al control, si el campo de conjunto de registros es Null, el cuadro de edición se establece en vacío. En una transferencia de control a conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.

Utilice las versiones con [CRecordset](../../mfc/reference/crecordset-class.md) parámetros si está trabajando con las clases basadas en ODBC. Utilice las versiones con [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) parámetros si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y más información sobre DDX para los campos [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) vea el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros .

### <a name="example"></a>Ejemplo

La `DoDataExchange` siguiente función para un [CRecordView](../../mfc/reference/crecordview-class.md) `DDX_FieldText` contiene `IDC_COURSELIST` llamadas de función para tres tipos de datos: es un cuadro combinado; los otros dos controles son cuadros de edición. Para la programación DAO, el parámetro *m_pSet* es un puntero a un [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)
