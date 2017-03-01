---
title: "Rutinas de validación de datos de cuadro de diálogo estándar | Documentos de Microsoft"
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
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
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
ms.openlocfilehash: 87cf0389b7b58579a8674d4075d2601186b1ae95
ms.lasthandoff: 02/24/2017

---
# <a name="standard-dialog-data-validation-routines"></a>Rutinas de validación de datos de cuadros de diálogo estándar
Este tema enumeran las rutinas de validación (DDV) de datos de cuadro de diálogo estándar utilizadas para los controles de cuadro de diálogo comunes de MFC.  
  
> [!NOTE]
>  Las rutinas de intercambio de datos de cuadro de diálogo estándar se definen en el afxdd_.h del archivo de encabezado. Sin embargo, las aplicaciones deben incluir afxwin.h.  
  
### <a name="ddv-functions"></a>Funciones DDV  
  
|||  
|-|-|  
|[DDV_MaxChars](#ddv_maxchars)|Comprueba que el número de caracteres de un valor determinado de control no supere un máximo especificado.|  
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Comprueba el valor de un control determinado no supere un determinado **bytes** intervalo.|  
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Comprueba el que valor de un control determinado no supere un determinado intervalo de tiempo.|  
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Comprueba el valor de un control determinado no supere un determinado **doble** intervalo.|  
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Comprueba el valor de un control determinado no supere un determinado **DWORD** intervalo.|  
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Comprueba el valor de un control determinado no supere un determinado **float** intervalo.|  
|[DDV_MinMaxInt](#ddv_minmaxint)|Comprueba el valor de un control determinado no supere un determinado **int** intervalo.|  
|[DDV_MinMaxLong](#ddv_minmaxlong)|Comprueba el valor de un control determinado no supere un determinado **largo** intervalo.|  
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Comprueba el valor de un control determinado no supere un determinado **LONGLONG** intervalo.|  
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Comprueba el que valor de un control determinado no supera un intervalo de fechas determinado.|  
|[DDV_MinMaxShort](#ddv_minmaxshort)|Comprueba el valor de un control determinado no supere un determinado **breve** intervalo.|  
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Comprueba que el valor de un control deslizante determinado se encuentra dentro del intervalo especificado.|  
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Comprueba el valor de un control determinado no supere un determinado **UINT** intervalo.|  
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Comprueba el valor de un control determinado no supere un determinado **ULONGLONG** intervalo.|  
  

  
##  <a name="a-nameddvmaxcharsa--ddvmaxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars  
 Llame a `DDV_MaxChars` para comprobar que la cantidad de caracteres en el control asociado *valor* no supere *nChars*.  
  
```   
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,  
    CString const& value,  
    int nChars); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `nChars`  
 Número máximo de caracteres permitidos.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxbytea--ddvminmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte  
 Llame a `DDV_MinMaxByte` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,  
    BYTE value,  
    BYTE minVal,  
    BYTE maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo **bytes**) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo **bytes**) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxdatetimea--ddvminmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime  
 Llame a `DDV_MinMaxDateTime` para comprobar que el valor de fecha y hora en el selector de fecha y hora control ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) asociado a *refValue* entre `refMinRange` y `refMaxRange`.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección. No es necesario eliminar este objeto.  
  
 *refValue*  
 Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) o [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto asociado a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control. Este objeto contiene los datos que se va a validar.  
  
 `refMinRange`  
 Mínimo valor permitido de fecha y hora.  
  
 `refMaxRange`  
 Valor de fecha y hora máximo permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxdoublea--ddvminmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble  
 Llame a `DDV_MinMaxDouble` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,  
    double const& value,  
    double minVal,  
    double maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo **doble**) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo **doble**) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxdworda--ddvminmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord  
 Llame a `DDV_MinMaxDWord` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,  
    DWORD const& value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo `DWORD`) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo `DWORD`) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxfloata--ddvminmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat  
 Llame a `DDV_MinMaxFloat` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,  
    float value,  
    float minVal,  
    float maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo **float**) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo **float**) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxinta--ddvminmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt  
 Llame a `DDV_MinMaxInt` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,  
    int value,  
    int minVal,  
    int maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo `int`) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo `int`) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxlonga--ddvminmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong  
 Llame a `DDV_MinMaxLong` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,  
    long value,  
    long minVal,  
    long maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo **largo**) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo **largo**) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxlonglonga--ddvminmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong  
 Llame a `DDV_MinMaxLongLong` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,  
    LONGLONG value,  
    LONGLONG minVal,  
    LONGLONG maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo **LONGLONG**) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo **LONGLONG**) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxmontha--ddvminmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth  
 Llame a `DDV_MinMaxMonth` para comprobar que el valor de fecha y hora en el calendario mensual control ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) asociado a *refValue* entre `refMinRange` y `refMaxRange`.  
  
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
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *refValue*  
 Una referencia a un objeto de tipo `CTime` o `COleDateTime` asociado a una variable de miembro del cuadro de diálogo, vista de formulario o control objeto view. Este objeto contiene los datos que se va a validar. Fases de MFC esta referencia cuando `DDV_MinMaxMonth` se llama.  
  
 `refMinRange`  
 Mínimo valor permitido de fecha y hora.  
  
 `refMaxRange`  
 Valor de fecha y hora máximo permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxshorta--ddvminmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort  
 Llame a `DDV_MinMaxShort` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,  
    short value,  
    short minVal,  
    short maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo **breve**) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo **breve**) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxslidera--ddvminmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider  
 Llame a `DDV_MinMaxSlider` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,  
    DWORD value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia al valor que se va a validar. Este parámetro contiene o establece la posición de control de posición actual del control deslizante.  
  
 `minVal`  
 Valor mínimo permitido.  
  
 `maxVal`  
 Valor máximo permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md). Para obtener información acerca de los controles deslizantes, consulte [CSliderCtrl utilizando](../../mfc/using-csliderctrl.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxuinta--ddvminmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt  
 Llame a `DDV_MinMaxUInt` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,  
    UINT value,  
    UINT minVal,  
    UINT maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo **UINT**) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo **UINT**) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
  
##  <a name="a-nameddvminmaxulonglonga--ddvminmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong  
 Llame a `DDV_MinMaxULongLong` para comprobar que el valor en el control asociado *valor* entre `minVal` y `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,  
    ULONGLONG value,  
    ULONGLONG  minVal ,  
    ULONGLONG  maxVal); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDX`  
 Puntero a un objeto `CDataExchange` . El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.  
  
 *value*  
 Una referencia a una variable de miembro del cuadro de diálogo, la vista de formulario o el objeto de vista del control con la que se validan los datos.  
  
 `minVal`  
 Valor mínimo (de tipo **ULONGLONG**) permitido.  
  
 `maxVal`  
 Valor máximo (de tipo **ULONGLONG**) permitido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdd_.h  
    
## <a name="see-also"></a>Vea también  
 [Rutinas de intercambio de datos de cuadro de diálogo estándar](../../mfc/reference/standard-dialog-data-exchange-routines.md)   
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

