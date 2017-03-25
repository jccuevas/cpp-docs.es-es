---
title: "Funciones de intercambio de datos de cuadro de diálogo para controles OLE | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
- OLE controls, DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 5c50690c1652c4136b7f52f852ddf201c9dd6c9b
ms.lasthandoff: 03/17/2017

---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funciones de intercambio de datos de cuadro de diálogo para controles OLE
En este tema se enumera las funciones DDX_OC utilizadas para intercambiar datos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
### <a name="ddxoc-functions"></a>Funciones DDX_OC  
  
|||  
|-|-|  
|[DDX_OCBool](#ddx_ocbool)|Administra la transferencia de **BOOL** datos entre una propiedad de un control OLE y un **BOOL** miembro de datos.|  
|[DDX_OCBoolRO](#ddx_ocboolro)|Administra la transferencia de **BOOL** datos entre una propiedad de sólo lectura de un control OLE y un **BOOL** miembro de datos.|  
|[DDX_OCColor](#ddx_occolor)|Administra la transferencia de **OLE_COLOR** datos entre una propiedad de un control OLE y un **OLE_COLOR** miembro de datos.|  
|[DDX_OCColorRO](#ddx_occolorro)|Administra la transferencia de **OLE_COLOR** datos entre una propiedad de sólo lectura de un control OLE y un **OLE_COLOR** miembro de datos.|  
|[DDX_OCFloat](#ddx_ocfloat)|Administra la transferencia de **float** (o **doble**) datos entre una propiedad de un control OLE y un **float** (o **doble**) miembro de datos.|  
|[DDX_OCFloatRO](#ddx_ocfloatro)|Administra la transferencia de **float** (o **doble**) datos entre una propiedad de sólo lectura de un control OLE y un **float** (o **doble**) miembro de datos.|  
|[DDX_OCInt](#ddx_ocint)|Administra la transferencia de `int` (o **largo**) datos entre una propiedad de un control OLE y un `int` (o **largo**) miembro de datos.|  
|[DDX_OCIntRO](#ddx_ocintro)|Administra la transferencia de `int` (o **largo**) datos entre una propiedad de sólo lectura de un control OLE y un `int` (o **largo**) miembro de datos.|  
|[DDX_OCShort](#ddx_ocshort)|Administra la transferencia de **corto** datos entre una propiedad de un control OLE y un **breve** miembro de datos.|  
|[DDX_OCShortRO](#ddx_ocshortro)|Administra la transferencia de **corto** datos entre una propiedad de sólo lectura de un control OLE y un **breve** miembro de datos.|  
|[DDX_OCText](#ddx_octext)|Administra la transferencia de **CString** datos entre una propiedad de un control OLE y un **CString** miembro de datos.|  
|[DDX_OCTextRO](#ddx_octextro)|Administra la transferencia de **CString** datos entre una propiedad de sólo lectura de un control OLE y un **CString** miembro de datos.|  
  
##  <a name="ddx_ocbool"></a>DDX_OCBool  
 El `DDX_OCBool` administra la transferencia de la función **BOOL** formularios de datos entre una propiedad de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un **BOOL** miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
```   
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado:** afxdisp.h  
  
##  <a name="ddx_ocboolro"></a>DDX_OCBoolRO  
 El `DDX_OCBoolRO` administra la transferencia de la función **BOOL** formularios de datos entre una propiedad de sólo lectura de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un **BOOL** miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
```   
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_occolor"></a>DDX_OCColor  
 El `DDX_OCColor` administra la transferencia de la función **OLE_COLOR** formularios de datos entre una propiedad de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un **OLE_COLOR** miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
```   
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_occolorro"></a>DDX_OCColorRO  
 El `DDX_OCColorRO` administra la transferencia de la función **OLE_COLOR** formularios de datos entre una propiedad de sólo lectura de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un **OLE_COLOR** miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
```   
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_ocfloat"></a>DDX_OCFloat  
 El `DDX_OCFloat` administra la transferencia de la función **float** (o **doble**) formularios de datos entre una propiedad de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un **float** (o **doble**) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
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
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_ocfloatro"></a>DDX_OCFloatRO  
 El `DDX_OCFloatRO` administra la transferencia de la función **float** (o **doble**) formularios de datos entre una propiedad de sólo lectura de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un **float** (o **doble**) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
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
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_ocint"></a>DDX_OCInt  
 El `DDX_OCInt` administra la transferencia de la función `int` (o **largo**) formularios de datos entre una propiedad de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un `int` (o **largo**) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
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
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_ocintro"></a>DDX_OCIntRO  
 El `DDX_OCIntRO` administra la transferencia de la función `int` (o **largo**) formularios de datos entre una propiedad de sólo lectura de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un `int` (o **largo**) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
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
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_ocshort"></a>DDX_OCShort  
 El `DDX_OCShort` función administra la transferencia de datos cortos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario, o el objeto de vista de control y un miembro de datos corto del cuadro de diálogo, vista de formulario o control objeto view.  
  
```   
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_ocshortro"></a>DDX_OCShortRO  
 El `DDX_OCShortRO` función administra la transferencia de datos cortos entre una propiedad de sólo lectura de un control OLE en un cuadro de diálogo, vista de formulario, o el objeto de vista de control y un miembro de datos corto del cuadro de diálogo, vista de formulario o control objeto view.  
  
```   
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_octext"></a>DDX_OCText  
 El **DDX_OCText** administra la transferencia de la función **CString** formularios de datos entre una propiedad de un control OLE en un cuadro de diálogo, vista o el objeto de vista de control y un **CString** miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista del control.  
  
```   
void AFXAPI DDX_OCText(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Un puntero a un **CDataExchange** objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="ddx_octextro"></a>DDX_OCTextRO  
 La función `DDX_OCTextRO` administra la transferencia de datos `CString` entre una propiedad de solo lectura de un control OLE de un objeto de cuadro de diálogo, vista de formulario o vista de control y un miembro de datos `CString` del objeto de cuadro de dialogo, vista de formulario o vista de control.  
  
```  
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 Identificador de un control OLE en el objeto de cuadro de diálogo, vista de formulario o vista de control.  
  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

