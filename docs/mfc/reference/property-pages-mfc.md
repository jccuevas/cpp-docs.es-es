---
title: "Páginas de propiedades (MFC) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages, global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
caps.latest.revision: 14
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
ms.openlocfilehash: 50888697fe01d3a84d9aa4c6f5f92926e4681535
ms.lasthandoff: 02/24/2017

---
# <a name="property-pages-mfc"></a>Páginas de propiedades (MFC)
Páginas de propiedades muestran los valores actuales de las propiedades de control OLE específicos en una interfaz gráfica y personalizable para ver y editar proporcionando un mecanismo de asignación de datos basado en el intercambio de datos de cuadro de diálogo (DDX).  
  
 Este mecanismo de asignación de datos asigna controles de la página de propiedades a las propiedades individuales del control OLE. El valor de la propiedad del control refleja el estado o el contenido del control de página de propiedades. La asignación entre las propiedades y los controles de la página de propiedad especificada por **DDP_** función llama a la página de propiedades `DoDataExchange` función miembro. La siguiente es una lista de **DDP_** funciones que intercambian datos introducidos mediante la página de propiedades del control:  
  
### <a name="property-page-data-transfer"></a>Transferencia de datos de la página de propiedad  
  
|||  
|-|-|  
|[DDP_CBIndex](#ddp_cbindex)|Vincula el índice de la cadena seleccionada en un cuadro combinado con la propiedad de un control.|  
|[DDP_CBString](#ddp_cbstring)|Vincula la cadena seleccionada en un cuadro combinado con la propiedad de un control. La cadena seleccionada puede comenzar con las mismas letras que el valor de propiedad pero no necesita coincidir completamente.|  
|[DDP_CBStringExact](#ddp_cbstringexact)|Vincula la cadena seleccionada en un cuadro combinado con la propiedad de un control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|  
|[DDP_Check](#ddp_check)|Una casilla de verificación en la página de propiedades del control con la propiedad de un control de vínculos.|  
|[DDP_LBIndex](#ddp_lbindex)|Vincula el índice de la cadena seleccionada en un cuadro de lista con la propiedad de un control.|  
|[DDP_LBString](#ddp_lbstring)|Vincula la cadena seleccionada en un cuadro de lista con la propiedad de un control. La cadena seleccionada puede comenzar con las mismas letras que el valor de propiedad pero no necesita coincidir completamente.|  
|[DDP_LBStringExact](#ddp_lbstringexact)|Vincula la cadena seleccionada en un cuadro de lista con la propiedad de un control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|  
|[DDP_PostProcessing](#ddp_postprocessing)|Finaliza a la transferencia de valores de propiedad de su control.|  
|[DDP_Radio](#ddp_radio)|Un grupo de botones de radio en la página de propiedades del control con la propiedad de un control de vínculos.|  
|[DDP_TEXT](#ddp_text)|Un control en la página de propiedades del control con la propiedad de un control de vínculos. Esta función controla los distintos tipos de propiedades, como **doble**, **corto**, `BSTR`, y **largo**.|  
  
 Para obtener más información acerca de la `DoDataExchange` páginas de propiedades y función, vea el artículo [controles ActiveX: páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).  
  
 La siguiente es una lista de macros que se utiliza para crear y administrar páginas de propiedades de un control OLE:  
  
### <a name="property-pages"></a>Páginas de propiedades  
  
|||  
|-|-|  
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Comienza la lista de identificadores de la página de propiedades.|  
|[END_PROPPAGEIDS](#end_proppageids)|Finaliza la lista de identificadores de la página de propiedades.|  
|[PROPPAGEID](#proppageid)|Declara una página de propiedades de la clase del control.|  
  
##  <a name="a-nameddpcbindexa--ddpcbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex  
 Llame a esta función en la página de propiedades `DoDataExchange` (función) para sincronizar el valor de una propiedad de entero con el índice de la selección actual en un cuadro combinado en la página de propiedades.  
  
```   
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso de combinado cuadro control asociado a la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con el control de cuadro combinado especificado por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_CBIndex` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddpcbstringa--ddpcbstring"></a><a name="ddp_cbstring"></a>DDP_CBString  
 Llame a esta función en la página de propiedades `DoDataExchange` función sincronizar el valor de una propiedad de cadena con la selección actual en un cuadro combinado en la página de propiedades.  
  
```  
void AFXAPI DDP_CBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso de combinado cuadro control asociado a la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con la cadena del cuadro combinado especificada por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_CBString` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddpcbstringexacta--ddpcbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact  
 Llame a esta función en la página de propiedades `DoDataExchange` (función) para sincronizar el valor de una propiedad de cadena que coincida exactamente con la selección actual en un cuadro combinado en la página de propiedades.  
  
```  
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso de combinado cuadro control asociado a la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con la cadena del cuadro combinado especificada por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_CBStringExact` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddpchecka--ddpcheck"></a><a name="ddp_check"></a>DDP_Check  
 Llame a esta función en la página de propiedades `DoDataExchange` función sincronizar el valor de la propiedad con el control de casilla de la página de propiedad asociada.  
  
```   
void AFXAPI DDP_Check(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso del control de casilla de verificación asociada a la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con el control de casilla de verificación especificado por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_Check` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddplbindexa--ddplbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex  
 Llame a esta función en la página de propiedades `DoDataExchange` (función) para sincronizar el valor de una propiedad de entero con el índice de la selección actual en un cuadro de lista en la página de propiedades.  
  
```   
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso de la lista cuadro control asociado a la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con la cadena del cuadro de lista especificada por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_LBIndex` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddplbstringa--ddplbstring"></a><a name="ddp_lbstring"></a>DDP_LBString  
 Llame a esta función en la página de propiedades `DoDataExchange` función sincronizar el valor de una propiedad de cadena con la selección actual en un cuadro de lista en la página de propiedades.  
  
```   
void AFXAPI DDP_LBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso de la lista cuadro control asociado a la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con la cadena del cuadro de lista especificada por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_LBString` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddplbstringexacta--ddplbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact  
 Llame a esta función en la página de propiedades `DoDataExchange` (función) para sincronizar el valor de una propiedad de cadena que coincida exactamente con la selección actual en un cuadro de lista en la página de propiedades.  
  
```   
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso de la lista cuadro control asociado a la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con la cadena del cuadro de lista especificada por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_LBStringExact` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddppostprocessinga--ddppostprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing  
 Llame a esta función en la página de propiedades `DoDataExchange` función, para finalizar la transferencia de valores de propiedad de la página de propiedades al control cuando se guardan los valores de propiedad.  
  
```   
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse una vez completadas todas las funciones de intercambio de datos. Por ejemplo:  
  
 [!code-cpp[NVC_MFCAxCtl&#15;](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddpradioa--ddpradio"></a><a name="ddp_radio"></a>DDP_Radio  
 Llame a esta función en el control `DoPropExchange` función sincronizar el valor de la propiedad con el control de botón de radio de página de propiedades asociada.  
  
```   
void AFXAPI DDP_Radio(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso de la radio button control asociado a la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con el control de botón de radio especificado por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_Radio` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameddptexta--ddptext"></a><a name="ddp_text"></a>DDP_TEXT  
 Llame a esta función en el control `DoDataExchange` función sincronizar el valor de la propiedad con el control de la página de propiedades asociada.  
  
```   
void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    BYTE & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    UINT & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    long & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    DWORD & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    float & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    double & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    CString & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `id`  
 El identificador de recurso del control asociado con la propiedad de control especificada por `pszPropName`.  
  
 `member`  
 La variable de miembro asociada al control de la página de propiedad especificado por `id` y la propiedad especificada por `pszPropName`.  
  
 `pszPropName`  
 El nombre de la propiedad del control que se intercambien con el control especificado por `id`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes correspondiente `DDX_Text` llamada de función.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-namebeginproppageidsa--beginproppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS  
 Inicia la definición de la lista del control de Id. de página de propiedades.  
  
```   
BEGIN_PROPPAGEIDS(class_name,  count)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control para la propiedad que se especifican las páginas.  
  
 *count*  
 El número de páginas de propiedades de la clase del control.  
  
### <a name="remarks"></a>Comentarios  
 En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, iniciar la lista de la página de propiedades con el `BEGIN_PROPPAGEIDS` (macro), a continuación, agregue entradas de macro para cada una de las páginas de propiedades y completar la lista de la página de propiedades con el `END_PROPPAGEIDS` (macro).  
  
 Para obtener más información sobre las páginas de propiedades, vea el artículo [controles ActiveX: páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameendproppageidsa--endproppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS  
 Termina la definición de su lista de Id. de página de propiedades.  
  
```   
END_PROPPAGEIDS(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control que posee la página de propiedades.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameproppageida--proppageid"></a><a name="proppageid"></a>PROPPAGEID  
 Agrega una página de propiedades para su uso por el control OLE.  
  
```   
PROPPAGEID(clsid)   
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 El identificador de clase único de una página de propiedades.  
  
### <a name="remarks"></a>Comentarios  
 Todos los `PROPPAGEID` las macros deben colocarse entre el `BEGIN_PROPPAGEIDS` y `END_PROPPAGEIDS` macros en el archivo de implementación del control.  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

