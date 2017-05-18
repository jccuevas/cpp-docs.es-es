---
title: COleDateTimeSpan (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
dev_langs:
- C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 0c696f59a6f4be7b4d966aad2a16a846d737009f
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan (clase)
Representa un tiempo relativo, un intervalo de tiempo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class COleDateTimeSpan
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Construye un objeto `COleDateTimeSpan`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDateTimeSpan::Format](#format)|Genera una representación de cadena con formato de un `COleDateTimeSpan` objeto.|  
|[COleDateTimeSpan::GetDays](#getdays)|Devuelve la parte correspondiente al día del intervalo de esta `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetHours](#gethours)|Devuelve la parte de hora del intervalo esto `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetMinutes](#getminutes)|Devuelve la parte de minutos del intervalo de esta `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetSeconds](#getseconds)|Devuelve la segunda parte del intervalo de esta `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetStatus](#getstatus)|Obtiene el estado (validez) de este `COleDateTimeSpan` objeto.|  
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Devuelve el número de días esto `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Devuelve el número de horas esto `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Devuelve el número de minutos esto `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Devuelve el número de segundos que este `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Establece el valor de este `COleDateTimeSpan` objeto.|  
|[COleDateTimeSpan::SetStatus](#setstatus)|Establece el estado (validez) de este `COleDateTimeSpan` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|||  
|-|-|  
|[operador +, -](#operator_add_-)|Agregar, restar y cambiar el inicio de sesión para `COleDateTimeSpan` valores.|  
|[operador +=-=](#operator_add_eq_-_eq)|La suma y resta un `COleDateTimeSpan` valor de este `COleDateTimeSpan` valor.|  
|[operador =](#operator_eq)|Copia un `COleDateTimeSpan` valor.|  
|[operador ==,<,></,><>](#coledatetimespan_relational_operators)|Comparar dos `COleDateTimeSpan` valores.|  
|[operador double](#operator_double)|Convierte este `COleDateTimeSpan` valor a un **doble**.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDateTimeSpan::m_span](#m_span)|Contiene subyacente **doble** para este `COleDateTimeSpan` objeto.|  
|[COleDateTimeSpan::m_status](#m_status)|Contiene el estado de este `COleDateTimeSpan` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `COleDateTimeSpan`no tiene una clase base.  
  
 Un `COleDateTimeSpan` hace tiempo en días.  
  
 `COleDateTimeSpan`se utiliza con su clase complementaria [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime`encapsula el **fecha** tipo de datos de automatización OLE. `COleDateTime`representa los valores de tiempo absoluto. Todos los `COleDateTime` implican cálculos `COleDateTimeSpan` valores. La relación entre estas clases es análoga a uno entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).  
  
 Para obtener más información sobre la `COleDateTime` y `COleDateTimeSpan` las clases, consulte el artículo [fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ATLComTime.h  
  
##  <a name="coledatetimespan_relational_operators"></a>Operadores relacionales COleDateTimeSpan  
 Operadores de comparación.  
  
```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *dateSpan*  
 `COleDateTimeSpan` que se va comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Estos operadores comparan dos valores de fecha/hora-span y devuelven **true** si la condición es true; en caso contrario **false**.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Si alguno de los operandos no es válida, se producirá un ATLASSERT.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]  
  
 [!code-cpp[26 de # NVC_ATLMFC_Utilities](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]  
  
##  <a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan  
 Construye un objeto `COleDateTimeSpan`.  
  
```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dblSpanSrc`  
 El número de días que se copiará en el nuevo `COleDateTimeSpan` objeto.  
  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 Indique los valores de día y hora que se copiará en el nuevo `COleDateTimeSpan` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Todos estos constructores crear nuevos `COleDateTimeSpan` objetos inicializados en el valor especificado. A continuación se ofrece una breve descripción de cada uno de estos constructores:  
  
- **() COleDateTimeSpan** construye una `COleDateTimeSpan` objeto se inicializa en 0.  
  
- **COleDateTimeSpan (** `dblSpanSrc` **)** construye una `COleDateTimeSpan` objeto de un valor de punto flotante.  
  
- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** construye una `COleDateTimeSpan` objeto inicializado en los valores numéricos especificados.  
  
 El estado de la nueva `COleDateTimeSpan` objeto está establecido a válido.  
  
 Para obtener más información acerca de los límites de `COleDateTimeSpan` valores, vea el artículo [fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]  
  
##  <a name="format"></a>COleDateTimeSpan::Format  
 Genera una representación de cadena con formato de un `COleDateTimeSpan` objeto.  
  
```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `pFormat`  
 Un formato de cadena similar a la `printf` cadena de formato. Códigos de formato, precedidos por un porcentaje ( `%`) inicie sesión, se ha reemplazado por el correspondiente `COleDateTimeSpan` componente. Otros caracteres en la cadena de formato se copian sin cambios en la cadena devuelta. El valor y el significado de los códigos de formato **formato** se enumeran a continuación:  
  
- **%H** horas del día actual  
  
- **%M** minutos durante la hora actual  
  
- **%S** segundos en el minuto actual  
  
- **%%**Signo de porcentaje  
  
 Los cuatro códigos de formato enumerados anteriormente son los códigos únicos que aceptará el formato.  
  
-  
  
 `nID`  
 El identificador de recurso para la cadena de formato de control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el valor con formato de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a estas funciones para crear una representación con formato del valor de intervalo de tiempo. Si el estado de este `COleDateTimeSpan` objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena devuelta es especificada por el recurso de cadena **IDS_INVALID_DATETIMESPAN**.  
  
 A continuación se ofrece una breve descripción de los formularios para esta función:  
  
 **Format(** `pFormat` **)**  
 Este formulario da formato al valor usando la cadena de formato que contiene los códigos de formato especiales precedidos por un signo de porcentaje (%), como en `printf`. La cadena de formato se pasa como un parámetro a la función.  
  
 **Format(** `nID` **)**  
 Este formulario da formato al valor usando la cadena de formato que contiene los códigos de formato especiales precedidos por un signo de porcentaje (%), como en `printf`. La cadena de formato es un recurso. El Id. de este recurso de cadena se pasa como parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]  
  
##  <a name="getdays"></a>COleDateTimeSpan::GetDays  
 Recupera la parte de día de este valor de fecha o intervalo de tiempo.  
  
```
LONG GetDays() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La parte de día de este valor de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto los valores de este intervalo de función entre aproximadamente - 3,615,000 y 3,615,000.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities Nº 16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]  
  
##  <a name="gethours"></a>COleDateTimeSpan::GetHours  
 Recupera la parte de este valor de fecha/hora-intervalo de hora.  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La parte de horas de este valor de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de función entre - 23 y 23.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetDays](#getdays)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]  
  
##  <a name="getminutes"></a>COleDateTimeSpan::GetMinutes  
 Recupera la parte de este valor de fecha/hora-intervalo de minutos.  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La parte de minutos de este valor de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de función entre - 59 y 59.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]  
  
##  <a name="getseconds"></a>COleDateTimeSpan::GetSeconds  
 Recupera la segunda parte de este valor de fecha o intervalo de tiempo.  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La parte de segundos de este valor de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de función entre - 59 y 59.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]  
  
##  <a name="getstatus"></a>COleDateTimeSpan::GetStatus  
 Obtiene el estado (validez) de este `COleDateTimeSpan` objeto.  
  
```
DateTimeSpanStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de este `COleDateTimeSpan` valor.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto se define mediante la **DateTimeSpanStatus** tipo enumerado, que se define dentro de la `COleDateTimeSpan` clase.  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
};  
```  
  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleDateTimeSpan::valid** indica que el control `COleDateTimeSpan` objeto es válido.  
  
- **COleDateTimeSpan::invalid** indica que el control `COleDateTimeSpan` objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleDateTimeSpan::null** indica que el control `COleDateTimeSpan` objeto es null, es decir, que se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
 El estado de un `COleDateTimeSpan` objeto no es válido en los casos siguientes:  
  
-   Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante una operación de asignación aritmético, es decir, `+=` o `-=`.  
  
-   Si se le asignó un valor no válido para este objeto.  
  
-   Si el estado de este objeto se estableció explícitamente en no válido con `SetStatus`.  
  
 Para obtener más información acerca de las operaciones que puede establecer el estado como no válidos, consulte [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) y [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).  
  
 Para obtener más información acerca de los límites de `COleDateTimeSpan` valores, vea el artículo [fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays  
 Recupera el valor de fecha o intervalo de tiempo expresado en días.  
  
```
double GetTotalDays() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de fecha o intervalo de tiempo expresado en días. Aunque esta función es un prototipo para devolver un valor double, siempre devolverá un valor entero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de función entre aproximadamente - 3.65e6 y 3.65e6.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities Nº 20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]  
  
##  <a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours  
 Recupera el valor de fecha o intervalo de tiempo expresado en horas.  
  
```
double GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de fecha o intervalo de tiempo expresado en horas. Aunque esta función es un prototipo para devolver un valor double, siempre devolverá un valor entero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de función entre aproximadamente - 8.77e7 y 8.77e7.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [GetTotalDays](#gettotaldays).  
  
##  <a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes  
 Recupera el valor de fecha o intervalo de tiempo expresado en minutos.  
  
```
double GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de fecha o intervalo de tiempo expresado en minutos. Aunque esta función es un prototipo para devolver un valor double, siempre devolverá un valor entero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de función entre aproximadamente - 5.26e9 y 5.26e9.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [GetTotalDays](#gettotaldays).  
  
##  <a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds  
 Recupera este valor de fecha o intervalo de tiempo expresado en segundos.  
  
```
double GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este valor de fecha o intervalo de tiempo expresado en segundos. Aunque esta función es un prototipo para devolver un valor double, siempre devolverá un valor entero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos por esta función oscilan entre aproximadamente: 3.16e11 a 3.16e11.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [GetTotalDays](#gettotaldays).  
  
##  <a name="m_span"></a>COleDateTimeSpan::m_span  
 Subyacente **doble** valor para este `COleDateTime` objeto.  
  
```
double m_span;
```  
  
### <a name="remarks"></a>Comentarios  
 Este valor expresa la fecha o intervalo de tiempo en días.  
  
> [!CAUTION]
>  Cambie el valor en el **doble** miembro de datos cambiará el valor de esta `COleDateTimeSpan` objeto. No cambia el estado de este `COleDateTimeSpan` objeto.  
  
##  <a name="m_status"></a>COleDateTimeSpan::m_status  
 El tipo de este miembro de datos es el tipo enumerado **DateTimeSpanStatus**, que se define dentro de la `COleDateTimeSpan` clase.  
  
```
DateTimeSpanStatus m_status;
```  
  
### <a name="remarks"></a>Comentarios  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleDateTimeSpan::valid** indica que el control `COleDateTimeSpan` objeto es válido.  
  
- **COleDateTimeSpan::invalid** indica que el control `COleDateTimeSpan` objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleDateTimeSpan::null** indica que el control `COleDateTimeSpan` objeto es null, es decir, que se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
 El estado de un `COleDateTimeSpan` objeto no es válido en los casos siguientes:  
  
-   Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante una operación de asignación aritmético, es decir, `+=` o `-=`.  
  
-   Si se le asignó un valor no válido para este objeto.  
  
-   Si el estado de este objeto se estableció explícitamente en no válido con [SetStatus](#setstatus).  
  
 Para obtener más información acerca de las operaciones que puede establecer el estado como no válidos, consulte [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) y [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).  
  
> [!CAUTION]
>  Este miembro de datos es en situaciones de programación avanzadas. Debe utilizar las funciones de miembro en línea [GetStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para conocer más advertencias con respecto a este miembro de datos se establece explícitamente.  
  
 Para obtener más información acerca de los límites de `COleDateTimeSpan` valores, vea el artículo [fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_eq"></a>COleDateTimeSpan::operator =  
 Copia un `COleDateTimeSpan` valor.  
  
```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este operador de asignaciones sobrecargados copia el valor de fecha/hora-intervalo de origen en esto `COleDateTimeSpan` objeto.  
  
##  <a name="operator_add_-"></a>COleDateTimeSpan::operator +, -  
 Agregar, restar y cambiar el inicio de sesión para `COleDateTimeSpan` valores.  
  
```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Los dos primeros operadores le permiten agregar y restar valores de fecha o intervalo de tiempo. El tercer argumento le permite cambiar el signo de un valor de fecha o intervalo de tiempo.  
  
 Si alguno de los operandos es null, el estado del resultante `COleDateTimeSpan` valor es null.  
  
 Si cualquiera de los operandos no es válido y el otro no es null, el estado del resultante `COleDateTimeSpan` valor no es válido.  
  
 Para obtener más información sobre los valores de estado válido, no válido y null, vea el [m_status](#m_status) variable miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator +=-=  
 La suma y resta un `COleDateTimeSpan` valor de este `COleDateTimeSpan` valor.  
  
```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Estos operadores permiten agregar y restar valores de fecha/hora-intervalo de esta `COleDateTimeSpan` objeto. Si alguno de los operandos es null, el estado del resultante `COleDateTimeSpan` valor es null.  
  
 Si cualquiera de los operandos no es válido y el otro no es null, el estado del resultante `COleDateTimeSpan` valor no es válido.  
  
 Para obtener más información sobre los valores de estado válido, no válido y null, vea el [m_status](#m_status) variable miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]  
  
##  <a name="operator_double"></a>COleDateTimeSpan::operator dobles  
 Convierte este `COleDateTimeSpan` valor a un **doble**.  
  
```
operator double() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este operador devuelve el valor de esta `COleDateTimeSpan` valor como un número de punto flotante de días.  
  
##  <a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan  
 Establece el valor de este valor de fecha o intervalo de tiempo.  
  
```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 Indique los valores de intervalo de fechas y el intervalo de tiempo que se copiará en esto `COleDateTimeSpan` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para las funciones que consultar el valor de un `COleDateTimeSpan` de objetos, vea las funciones miembro siguientes:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]  
  
##  <a name="setstatus"></a>COleDateTimeSpan::SetStatus  
 Establece el estado (validez) de este `COleDateTimeSpan` objeto.  
  
```
void SetStatus(DateTimeSpanStatus status) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *status*  
 El nuevo valor de estado para esta `COleDateTimeSpan` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El *estado* el valor del parámetro se define mediante la **DateTimeSpanStatus** tipo enumerado, que se define dentro de la `COleDateTimeSpan` clase.  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleDateTimeSpan::valid** indica que el control `COleDateTimeSpan` objeto es válido.  
  
- **COleDateTimeSpan::invalid** indica que el control `COleDateTimeSpan` objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleDateTimeSpan::null** indica que el control `COleDateTimeSpan` objeto es null, es decir, que se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
    > [!CAUTION]
    >  Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Con más frecuencia se utilizará para establecer el estado en `null` o **válido**. Tenga en cuenta que el operador de asignación ( [operador =](#eq)) y [SetDateTimeSpan](#setdatetimespan) establecer el estado del objeto en función de los valores de origen.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [COleDateTime (clase)](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime (clase)](../../atl-mfc-shared/reference/ctime-class.md)   
 [Clase CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)



