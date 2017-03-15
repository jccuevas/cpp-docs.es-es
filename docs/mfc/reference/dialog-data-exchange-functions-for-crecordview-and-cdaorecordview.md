---
title: "Funciones de intercambio de datos de cuadro de diálogo para CRecordView y CDaoRecordView | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DDX_Field functions
- ODBC [C++], dialog data exchange (DDX) support
- DDX (dialog data exchange) [C++], database support
- DDX (dialog data exchange) [C++], functions
- databases [C++], dialog data exchange (DDX) support
- DAO [C++], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 682c845aa2c915be69aee0d5e95f820573cd6084
ms.lasthandoff: 02/24/2017

---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funciones de intercambio de datos de cuadro de diálogo para CRecordView y CDaoRecordView
Este tema enumeran las funciones DDX_Field utilizadas para intercambiar datos entre un [CRecordset](../../mfc/reference/crecordset-class.md) y un [CRecordView](../../mfc/reference/crecordview-class.md) formulario o un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) y un [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) formulario.  
  
> [!NOTE]
>  DDX_Field (funciones) son como las funciones DDX que intercambian datos con controles en un formulario. Pero a diferencia de DDX, intercambiar datos con los campos del objeto de conjunto de registros asociado de la vista en lugar de con los campos de la vista del registro. Para obtener más información, consulte las clases `CRecordView` y `CDaoRecordView`.  
  
### <a name="ddxfield-functions"></a>DDX_Field (funciones)  
  
|||  
|-|-|  
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Transfiere datos enteros entre un miembro de datos de campo de conjunto de registros y el índice de la selección actual en un cuadro combinado en un [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|  
|[DDX_FieldCBString](#ddx_fieldcbstring)|Las transferencias de `CString` cuadro datos entre un miembro de datos de campo de conjunto de registros y el control de edición de un cuadro combinado un `CRecordView` o `CDaoRecordView`. Al mover datos desde el conjunto de registros para el control, esta función selecciona el elemento en el cuadro combinado que comienza con los caracteres de la cadena especificada.|  
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Las transferencias de `CString` cuadro datos entre un miembro de datos de campo de conjunto de registros y el control de edición de un cuadro combinado un `CRecordView` o `CDaoRecordView`. Al mover datos desde el conjunto de registros para el control, esta función selecciona el elemento en el cuadro combinado que coincide exactamente con la cadena especificada.|  
|[DDX_FieldCheck](#ddx_fieldcheck)|Transfiere datos booleanos entre un miembro de datos de campo de conjunto de registros y una casilla en un `CRecordView` o `CDaoRecordView`.|  
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Transfiere datos enteros entre un miembro de datos de campo de conjunto de registros y el índice de la selección actual en un cuadro de lista en un `CRecordView` o `CDaoRecordView`.|  
|[DDX_FieldLBString](#ddx_fieldlbstring)|Administra la transferencia de [CString](../../atl-mfc-shared/reference/cstringt-class.md) datos entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros. Al mover datos desde el conjunto de registros para el control, esta función selecciona el elemento en el cuadro de lista que comienza con los caracteres de la cadena especificada.|  
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Administra la transferencia de `CString` datos entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros. Al mover datos desde el conjunto de registros para el control, esta función selecciona el primer elemento que coincida exactamente con la cadena especificada.|  
|[DDX_FieldRadio](#ddx_fieldradio)|Transfiere datos enteros entre un miembro de datos de campo de conjunto de registros y un grupo de botones de opción en un `CRecordView` o `CDaoRecordView`.|  
|[DDX_FieldScroll](#ddx_fieldscroll)|Establece u obtiene la posición de desplazamiento de un control de barra de desplazamiento en un `CRecordView` o `CDaoRecordView`. Llamar desde su [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) (función).|  
|[DDX_FieldText](#ddx_fieldtext)|Versiones sobrecargadas están disponibles para la transferencia de `int`, **UINT**, **largo**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **doble**, **corto**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), y [COleCurrency](../../mfc/reference/colecurrency-class.md) cuadro datos entre un miembro de datos de campo de conjunto de registros y una operación de edición una `CRecordView` o `CDaoRecordView`.|  
  
##  <a name="a-nameddxfieldcbindexa--ddxfieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex  
 El `DDX_FieldCBIndex` función sincroniza el índice del elemento seleccionado en el control de cuadro de lista de un control de cuadro combinado en una vista de registros y un `int` miembro de datos de campo de un conjunto de registros asociado a la vista de registros.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *índice*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Al mover datos desde el conjunto de registros para el control, esta función establece la selección en el control basándose en el valor especificado en *índice*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, MFC establece el valor del índice 0. En una transferencia desde el control al conjunto de registros, si el control está vacío o si ningún elemento seleccionado, el campo de conjunto de registros se establece en 0.  
  
 Si trabaja con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión si trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. El ejemplo sería similar para `DDX_FieldCBIndex`.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  

##  <a name="a-nameddxfieldcbstringa--ddxfieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString  
 El `DDX_FieldCBString` administra la transferencia de la función [CString](../../atl-mfc-shared/reference/cstringt-class.md) datos entre el control de edición de un control de cuadro combinado en una vista de registros y un `CString` miembro de datos de campo de un conjunto de registros asociado a la vista de registros.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *value*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Al mover datos desde el conjunto de registros para el control, esta función establece la selección actual en el cuadro combinado a la primera fila que comienza con los caracteres de la cadena especificada en *valor*. En una transferencia desde el conjunto de registros para el control si el campo de conjunto de registros es Null, se quita cualquier selección de cuadro combinado y se establece el control de edición del cuadro combinado está vacío. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null si el campo permite.  
  
 Si trabaja con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión si trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. El ejemplo incluye una llamada a `DDX_FieldCBString`.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
## <a name="a-nameddxfieldcbstringexacta--ddxfieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact  
 El `DDX_FieldCBStringExact` administra la transferencia de la función [CString](../../atl-mfc-shared/reference/cstringt-class.md) datos entre el control de edición de un control de cuadro combinado en una vista de registros y un `CString` miembro de datos de campo de un conjunto de registros asociado a la vista de registros.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *value*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Al mover datos desde el conjunto de registros para el control, esta función establece la selección actual en el cuadro combinado a la primera fila que coincida exactamente con la cadena especificada en *valor*. En una transferencia desde el conjunto de registros para el control si el campo de conjunto de registros es NULL, se quita cualquier selección de cuadro combinado y se establece el cuadro de edición del cuadro combinado está vacío. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en NULL.  
  
 Si trabaja con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión si trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldCBStringExact` sería similar.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="a-nameddxfieldchecka--ddxfieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck  
 El `DDX_FieldCheck` administra la transferencia de la función `int` formularios de datos entre un control de casilla de verificación en un cuadro de diálogo, vista o el objeto de vista de control y un `int` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de casilla de verificación asociado a la propiedad de control.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian datos de objeto de vista de control.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_FieldCheck` se llama, *valor* se establece en el estado actual del control de casilla de verificación, o el estado del control se establece en *valor*, en función de la dirección de la transferencia.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="a-nameddxfieldlbindexa--ddxfieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex  
 El `DDX_FieldLBIndex` función sincroniza el índice del elemento seleccionado en un control de cuadro de lista en una vista de registros y un `int` miembro de datos de campo de un conjunto de registros asociado a la vista de registros.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *índice*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Al mover datos desde el conjunto de registros para el control, esta función establece la selección en el control basándose en el valor especificado en *índice*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, MFC establece el valor del índice 0. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en 0.  
  
 Si trabaja con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión si trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="a-nameddxfieldlbstringa--ddxfieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString  
 El `DDX_FieldLBString` copia la selección actual de un control de cuadro de lista en una vista de registros a una [CString](../../atl-mfc-shared/reference/cstringt-class.md) miembro de datos de campo de un conjunto de registros asociado a la vista de registros.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *value*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 En la dirección inversa, esta función establece la selección actual en el cuadro de lista a la primera fila que comienza con los caracteres de la cadena especificada por *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, se quita cualquier selección del cuadro de lista. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.  
  
 Si trabaja con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión si trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldLBString` sería similar.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="a-nameddxfieldlbstringexacta--ddxfieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact  
 El `DDX_FieldLBStringExact` función copia la selección actual de un control de cuadro de lista en una vista de registros a una [CString](../../atl-mfc-shared/reference/cstringt-class.md) miembro de datos de campo de un conjunto de registros asociado a la vista de registros.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *value*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 En la dirección inversa, esta función establece la selección actual en el cuadro de lista a la primera fila que coincida exactamente con la cadena especificada en *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, se quita cualquier selección del cuadro de lista. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.  
  
 Si trabaja con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión si trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldLBStringExact` sería similar.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="a-nameddxfieldradioa--ddxfieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio  
 El `DDX_FieldRadio` función asocia basado en cero `int` variable miembro del conjunto de registros de una vista de registros con el botón de radio seleccionado actualmente en un grupo de botones de radio en la vista de registros.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de la primera de un grupo (con estilo **WS_GROUP**) de los controles de botón de radio adyacentes en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *value*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se transfieren desde el campo de conjunto de registros a la vista, esta función se activará la *n* botón de radio (basado en cero) y se desactivan los otros botones. En la dirección inversa, esta función establece el campo de conjunto de registros en el número ordinal del botón de radio que se encuentra actualmente en (activada). En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, no se selecciona ningún botón. En una transferencia desde el control al conjunto de registros, si no se selecciona ningún control, el campo de conjunto de registros se establece en Null si el campo permite.  
  
 Si trabaja con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión si trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldRadio` sería similar.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="a-nameddxfieldscrolla--ddxfieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll  
 El `DDX_FieldScroll` función sincroniza la posición de desplazamiento de un control de barra de desplazamiento en una vista de registros y un `int` miembro de datos de campo de un conjunto de registros asociado a la vista de registros (o elige asignar a cualquier variable de entero).  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *nIDC\**  
 El identificador de la primera de un grupo (con estilo **WS_GROUP**) de los controles de botón de radio adyacentes en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *value*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Al mover datos desde el conjunto de registros para el control, esta función establece la posición de desplazamiento de la barra de desplazamiento en el valor especificado en *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, el control de barra de desplazamiento se establece en 0. En una transferencia desde el control al conjunto de registros, si el control está vacío, el valor del campo de conjunto de registros es 0.  
  
 Si trabaja con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión si trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldScroll` sería similar.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="a-nameddxfieldtexta--ddxfieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText  
 El `DDX_FieldText` administra la transferencia de la función `int`, **corto**, **largo**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **doble**, **BOOL**, o **bytes** datos entre un control de cuadro de edición y los miembros de datos de campo de un conjunto de registros.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.  
  
 *value*  
 Una referencia a un miembro de datos de campo en el `CRecordset` o `CDaoRecordset` objeto. El tipo de datos del valor dependerá de cuál de las versiones sobrecargadas de `DDX_FieldText` utiliza.  
  
 `pRecordset`  
 Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto con el que se intercambian los datos. This (puntero) permite `DDX_FieldText` para detectar y establecer valores Null.  
  
### <a name="remarks"></a>Comentarios  
 Para [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objetos, `DDX_FieldText` también administra la transferencia de [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), y [COleCurrency](../../mfc/reference/colecurrency-class.md) valores. Un control de cuadro de edición vacío indica un valor Null. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, se establece el cuadro de edición está vacío. En una transferencia desde el control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.  
  
 Utilice las versiones con [CRecordset](../../mfc/reference/crecordset-class.md) parámetros si se trabaja con las clases basadas en ODBC. Utilice las versiones con [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) parámetros si se trabaja con las clases basadas en DAO.  
  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, vea el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Ejemplo  
 El siguiente `DoDataExchange` funcionar por un [CRecordView](../../mfc/reference/crecordview-class.md) contiene `DDX_FieldText` función llama para tres tipos de datos: `IDC_COURSELIST` es un cuadro combinado; los otros dos controles son cuadros de edición. Para la programación de DAO, la *m_pSet* parámetro es un puntero a un [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 [!code-cpp[NVC_MFCDatabase&#43;](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]  

  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

