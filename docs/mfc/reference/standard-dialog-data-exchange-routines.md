---
title: "Rutinas de intercambio de datos de cuadro de diálogo estándar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 86491a06a81f5b0ddf0c91c9c5f2b5f23261b49b
ms.lasthandoff: 04/04/2017

---
# <a name="standard-dialog-data-exchange-routines"></a>Rutinas de intercambio de datos de cuadros de diálogo estándar
Este tema enumeran las rutinas de intercambio (DDX) de datos de cuadros de diálogo estándar utilizadas para los controles de cuadro de diálogo comunes de MFC.  
  
> [!NOTE]
>  Las rutinas de intercambio de datos de cuadro de diálogo estándar se definen en el afxdd_.h del archivo de encabezado. Sin embargo, las aplicaciones deben incluir afxwin.h.  
  
### <a name="ddx-functions"></a>DDX (funciones)  
  
|||  
|-|-|  
|[DDX_CBIndex](#ddx_cbindex)|Se inicializa o recupera el índice de la selección actual de un control de cuadro combinado.|  
|[DDX_CBString](#ddx_cbstring)|Se inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|  
|[DDX_CBStringExact](#ddx_cbstringexact)|Se inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|  
|[DDX_Check](#ddx_check)|Se inicializa o recupera el estado actual de un control de casilla de verificación.|  
|[DDX_Control](#ddx_control)|Subclases de un control determinado dentro de un cuadro de diálogo.|  
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Se inicializa o recupera datos de fecha y hora de un control de selector de fecha y hora.|  
|[DDX_IPAddress](#ddx_ipaddress)|Se inicializa o recupera el valor actual de un control de dirección IP.|  
|[DDX_LBIndex](#ddx_lbindex)|Se inicializa o recupera el índice de la selección actual de un control de cuadro de lista.|  
|[DDX_LBString](#ddx_lbstring)|Se inicializa o recupera la selección actual en un control de cuadro de lista.|  
|[DDX_LBStringExact](#ddx_lbstringexact)|Se inicializa o recupera la selección actual en un control de cuadro de lista.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Crea un control de .NET que coincida con identificador de recurso. del control|  
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Se inicializa o recupera el valor actual de un control de calendario mensual.|  
|[DDX_Radio](#ddx_radio)|Se inicializa o recupera el índice basado en 0 del control de radio que se está comprobando actualmente dentro de un grupo de control de radio.|  
|[DDX_Scroll](#ddx_scroll)|Se inicializa o recupera la posición actual del control de posición de un control de desplazamiento.|  
|[DDX_Slider](#ddx_slider)|Se inicializa o recupera la posición actual del control de posición del control deslizante.|  
|[DDX_Text](#ddx_text)|Se inicializa o recupera el valor actual de un control de edición.|  
  
##  <a name="ddx_cbindex"></a>DDX_CBIndex  
 El `DDX_CBIndex` función administra la transferencia de `int` datos entre un control de cuadro combinado en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `int` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
```  
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de cuadro combinado asociado a la propiedad de control.  
  
 *índice*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_CBIndex` se llama, *índice* se establece en el índice de la selección actual del cuadro combinado. Si se selecciona ningún elemento, *índice* se establece en 0.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_cbstring"></a>DDX_CBString  
 El `DDX_CBString` función administra la transferencia de `CString` datos entre el control de edición de un control de cuadro combinado en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `CString` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
```  
void AFXAPI DDX_CBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de cuadro combinado asociado a la propiedad de control.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_CBString` se llama, *valor* se establece en la selección actual del cuadro combinado. Si se selecciona ningún elemento, *valor* se establece en una cadena de longitud cero.  
  
> [!NOTE]
>  Si el cuadro combinado es un cuadro de lista desplegable, el valor intercambiado se limita a 255 caracteres.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_cbstringexact"></a>DDX_CBStringExact  
 El `DDX_CBStringExact` función administra la transferencia de `CString` datos entre el control de edición de un control de cuadro combinado en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `CString` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
```  
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de cuadro combinado asociado a la propiedad de control.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_CBStringExact` se llama, *valor* se establece en la selección actual del cuadro combinado. Si se selecciona ningún elemento, *valor* se establece en una cadena de longitud cero.  
  
> [!NOTE]
>  Si el cuadro combinado es un cuadro de lista desplegable, el valor intercambiado se limita a 255 caracteres.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_check"></a>DDX_Check  
 El `DDX_Check` función administra la transferencia de `int` datos entre un control de casilla de verificación en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `int` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
```  
void AFXAPI DDX_Check(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de casilla de verificación asociado a la propiedad de control.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_Check` se llama, *valor* se establece en el estado actual del control de casilla de verificación. Para obtener una lista de los valores de estado posibles, consulte [BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_control"></a>DDX_Control  
 El `DDX_Control` función subclases del control, especificado por `nIDC`, del cuadro de diálogo, vista de formulario o del objeto de vista de control.  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `nIDC`  
 El identificador de recurso del control que se pueden crear subclases.  
  
 *rControl*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control relacionada con el control especificado.  
  
### <a name="remarks"></a>Comentarios  
 El `pDX` objeto proporcionado por el marco de trabajo cuando el `DoDataExchange` función se invoca. Por lo tanto, `DDX_Control` solo debe llamarse dentro de la invalidación de `DoDataExchange`.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl  
 El `DDX_DateTimeCtrl` función administra la transferencia de datos de fecha y hora entre un control de selector de fecha y hora ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) en un objeto de vista de formulario o de cuadro de diálogo y, o bien un [CTime](../../atl-mfc-shared/reference/ctime-class.md) o un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) miembro de datos del objeto de vista de formulario o de cuadro de diálogo.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar el objeto.  
  
 `nIDC`  
 El identificador de recurso del control de selector de fecha y hora asociado a la variable miembro.  
  
 *value*  
 En las dos primeras versiones, una referencia a un `CTime` o `COleDateTime` variable miembro, cuadro de diálogo, vista de formulario o con el que se intercambian los datos de objeto de vista de control. En la tercera versión, una referencia a un `CString` objeto de vista de control de miembro de datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_DateTimeCtrl` se llama, *valor* se establece en el actual estado de la fecha y el control de selector de tiempo o el control se establece en *valor*, en función de la dirección del intercambio.  
  
 En la tercera versión anterior, `DDX_DateTimeCtrl` administra la transferencia de `CString` control datos entre una fecha y hora y un [CString](../../atl-mfc-shared/reference/cstringt-class.md) miembro de datos del objeto de vista de control. Formato de la cadena usando reglas de la configuración regional actual para dar formato a fechas y horas.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  

   

 
## <a name="ddx_managedcontrol"></a>DDX_ManagedControl
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
 `pDX`  
 Un puntero a un [CDataExchange (clase)](cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control asociado a la propiedad de control.  
  
 `control`  
 Una referencia a un [CWinFormsControl clase](cwinformscontrol-class.md) objeto.  
   
### <a name="remarks"></a>Comentarios  
 `DDX_ManagedControl`llamadas [CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) para crear un control que coincida con el identificador de control de recurso. Use `DDX_ManagedControl` para crear controles de identificadores de recursos en [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog). Para el intercambio de datos, no es necesario utilizar las funciones DDX/DDV con controles de formularios Windows Forms.  
  
 Para obtener más información, consulte [Cómo: realizar enlace de datos DDX/DDV con formularios Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h  
   
### <a name="see-also"></a>Vea también  
 [CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)   
 [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog)
 

  
##  <a name="ddx_ipaddress"></a>DDX_IPAddress  
 El `DDX_IPAddress` función administra la transferencia de datos entre un control de dirección IP y un miembro de datos del objeto de vista de control.  
  
```  
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de dirección IP asociado a la propiedad de control.  
  
 *value*  
 Una referencia a la `DWORD` que contiene el valor del campo de cuatro del control de dirección IP. Los campos se rellenan o quede como sigue.  
  
|Campo|Que contiene el valor del campo de bits|  
|-----------|-------------------------------------|  
|3|de 0 a 7|  
|2|8 a 15|  
|1|16 a 23|  
|0|24 a 31|  
  
 Utilizar Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378) para leer el valor o use [IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380) para rellenar el valor. Estos mensajes se describen en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_IPAddress` se llama, *valor* se lee desde el control de dirección IP, o *valor* se escribe en el control, dependiendo de la dirección del intercambio.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_lbindex"></a>DDX_LBIndex  
 El `DDX_LBIndex` función administra la transferencia de `int` datos entre un control de cuadro de lista en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `int` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
```  
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de cuadro de lista asociado a la propiedad de control.  
  
 *índice*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_LBIndex` se llama, *índice* se establece en el índice de la selección actual del cuadro de lista. Si se selecciona ningún elemento, *índice* se establece en -1.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_lbstring"></a>DDX_LBString  
 El `DDX_LBString` función administra la transferencia de `CString` datos entre un control de cuadro de lista en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `CString` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
```  
void AFXAPI DDX_LBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de cuadro de lista asociado a la propiedad de control.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_LBString` se llama para transferir datos a un control de cuadro de lista, el primer elemento en el control cuyo comienzo coincide con *valor* está seleccionada. (Para que coincida con el elemento completo en lugar de simplemente un prefijo, utilice [DDX_LBStringExact](#ddx_lbstringexact).) Si no hay ninguna coincidencia, se seleccionó ningún elemento. La coincidencia distingue entre mayúsculas y minúsculas.  
  
 Cuando `DDX_LBString` para transferir datos de un control de cuadro de lista, se llama *valor* se establece en la selección actual del cuadro de lista. Si se selecciona ningún elemento, *valor* se establece en una cadena de longitud cero.  
  
> [!NOTE]
>  Si el cuadro de lista es un cuadro de lista desplegable, el valor que se intercambian se limita a 255 caracteres.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_lbstringexact"></a>DDX_LBStringExact  
 El `DDX_CBStringExact` función administra la transferencia de `CString` datos entre el control de edición de un control de cuadro de lista en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `CString` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
```  
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de cuadro de lista asociado a la propiedad de control.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_LBStringExact` se llama para transferir datos a un control de cuadro de lista, el primer elemento en el control que coincida con *valor* está seleccionada. (Para que coincida con solo un prefijo en lugar de todo el elemento, utilice [DDX_LBString](#ddx_lbstring).) Si no hay ninguna coincidencia, se seleccionó ningún elemento. La coincidencia distingue entre mayúsculas y minúsculas.  
  
 Cuando `DDX_CBStringExact` para transferir datos de un control de cuadro de lista, se llama *valor* se establece en la selección actual del cuadro de lista. Si se selecciona ningún elemento, *valor* se establece en una cadena de longitud cero.  
  
> [!NOTE]
>  Si el cuadro de lista es un cuadro de lista desplegable, el valor que se intercambian se limita a 255 caracteres.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar el objeto.  
  
 `nIDC`  
 El identificador de recurso de control de calendario mensual asociado a la variable miembro.  
  
 *value*  
 Una referencia a un `CTime` o `COleDateTime` variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El control administra únicamente un valor de fecha. Los campos de hora en el objeto de tiempo son conjunto para reflejar la hora de creación de la ventana de control o la hora se estableció en el control con una llamada a `CMonthCalCtrl::SetCurSel`.  
  
 Cuando `DDX_MonthCalCtrl` se llama, *valor* se establece en el estado actual del control de calendario mensual.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_radio"></a>DDX_Radio  
 El `DDX_Radio` función administra la transferencia de `int` datos entre un grupo de controles de radio en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `int` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control. El valor de la `int` miembro de datos se determina según qué radio dentro del grupo está seleccionado.  
  
```  
void AFXAPI DDX_Radio(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del primer control de radio del grupo.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_Radio` se llama, *valor* se establece en el estado actual del grupo de control de radio. El valor se establece como un índice basado en 0 del control de radio que actualmente está activado, o -1 si ningún control de radio se comprueban.  
  
 Por ejemplo, en caso de que el primer botón de radio del grupo está activada (el botón con el estilo WS_GROUP) el valor de la `int` miembro es 0 y así sucesivamente.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_scroll"></a>DDX_Scroll  
 El `DDX_Scroll` función administra la transferencia de `int` datos entre un control de barra de desplazamiento en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un `int` miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
```  
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control de barra de desplazamiento asociado a la propiedad de control.  
  
 *value*  
 Referencia a una variable de miembro del objeto de cuadro de diálogo, vista de formulario o vista de control con el que se intercambian los datos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_Scroll` se llama, *valor* se establece en la posición actual del control de posición del control. Para obtener más información sobre los valores asociados a la posición actual del control de posición del control, vea [GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_slider"></a>DDX_Slider  
 El `DDX_Slider` función administra la transferencia de `int` datos entre un control deslizante en una vista de formulario o de cuadro de diálogo y un `int` miembro de datos del objeto de vista de formulario o de cuadro de diálogo.  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de recurso del control deslizante.  
  
 *value*  
 Una referencia al valor que se van a intercambiar. Este parámetro contiene o establece la posición actual del control deslizante.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `DDX_Slider` se llama, *valor* se establece en la posición actual del control de posición del control, o el valor recibe la posición, dependiendo de la dirección del intercambio.  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md). Para obtener información acerca de los controles deslizantes, consulte [usar CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="ddx_text"></a>DDX_Text  
 El `DDX_Text` función administra la transferencia de `int`, **UINT**, **largo**, `DWORD`, `CString`, **float**, o **doble** datos entre un control de edición en un cuadro de diálogo, vista de formulario o vista de control y un [CString](../../atl-mfc-shared/reference/cstringt-class.md) miembro de datos del cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 `nIDC`  
 El identificador de un control de edición en el cuadro de diálogo, la vista de formulario o el objeto de vista de control.  
  
 *value*  
 Una referencia a un miembro de datos en el cuadro de diálogo, la vista de formulario o el objeto de vista de control. Tipo de datos de *valor* depende de cuál de las versiones sobrecargadas de `DDX_Text` utiliza.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  

## <a name="see-also"></a>Vea también  
 [Rutinas de validación de datos de cuadros de diálogo estándar](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

