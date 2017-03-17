---
title: COleDateTimeSpan (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4091ca2c766d56d8398119413778af0a0405b8ab
ms.lasthandoff: 02/24/2017

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
|[COleDateTimeSpan::GetDays](#getdays)|Devuelve la parte de día del intervalo de este `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetHours](#gethours)|Devuelve la parte de hora del intervalo este `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetMinutes](#getminutes)|Devuelve la parte de minutos del intervalo de este `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetSeconds](#getseconds)|Devuelve la segunda parte del intervalo de este `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetStatus](#getstatus)|Obtiene el estado (validez) de este `COleDateTimeSpan` objeto.|  
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Devuelve el número de días este `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Devuelve el número de horas esto `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Devuelve el número de minutos este `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Devuelve el número de segundos este `COleDateTimeSpan` objeto representa.|  
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Establece el valor de este `COleDateTimeSpan` objeto.|  
|[COleDateTimeSpan::SetStatus](#setstatus)|Establece el estado (validez) de este `COleDateTimeSpan` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|||  
|-|-|  
|[operador +, -](#operator_add_-)|Agregar, restar y cambiar el signo de `COleDateTimeSpan` valores.|  
|[operador +=, =](#operator_add_eq_-_eq)|Sumar y restar un `COleDateTimeSpan` el valor de este `COleDateTimeSpan` valor.|  
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
  
 Para obtener más información sobre la `COleDateTime` y `COleDateTimeSpan` clases, vea el artículo [fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ATLComTime.h  
  
##  <a name="coledatetimespan_relational_operators"></a>Operadores relacionales de COleDateTimeSpan  
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
 Estos operadores comparan dos valores de fecha o intervalo de tiempo y devuelven **true** si la condición es true; en caso contrario **false**.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Si alguno de los operandos no es válido, se producirá un ATLASSERT.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities&#25;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]  
  
 [!code-cpp[26 de NVC_ATLMFC_Utilities #](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]  
  
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
 Todos estos constructores crean nuevos `COleDateTimeSpan` objetos inicializados en el valor especificado. A continuación se muestra una breve descripción de cada uno de estos constructores:  
  
- **() COleDateTimeSpan** construye un `COleDateTimeSpan` objeto se inicializa en 0.  
  
- **COleDateTimeSpan (** `dblSpanSrc` **)** construye un `COleDateTimeSpan` objeto de un valor de punto flotante.  
  
- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** construye un `COleDateTimeSpan` objeto inicializado con los valores numéricos especificados.  
  
 El estado de la nueva `COleDateTimeSpan` objeto está establecido a válido.  
  
 Para obtener más información acerca de los límites de `COleDateTimeSpan` valores, vea el artículo [fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities&#14;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]  
  
##  <a name="format"></a>COleDateTimeSpan::Format  
 Genera una representación de cadena con formato de un `COleDateTimeSpan` objeto.  
  
```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `pFormat`  
 Un formato de cadena similar a la `printf` cadena de formato. Códigos de formato, precedidos por un porcentaje ( `%`) inicie sesión, se reemplazan por el correspondiente `COleDateTimeSpan` componente. Otros caracteres de la cadena de formato se copian sin cambios a la cadena devuelta. El valor y el significado de los códigos de formato de **formato** se enumeran a continuación:  
  
- **%H** horas al día de hoy  
  
- **%M** minutos durante la hora actual  
  
- **%S** segundos en el minuto actual  
  
- **%%**Signo de porcentaje  
  
 Los códigos de formato de cuatro mencionados anteriormente son los códigos únicos que aceptará el formato.  
  
-  
  
 `nID`  
 El identificador de recurso de la cadena de formato de control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el valor con formato de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a estas funciones para crear una representación con formato del valor de intervalo de tiempo. Si el estado de este `COleDateTimeSpan` objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena devuelta es especificada por el recurso de cadena **IDS_INVALID_DATETIMESPAN**.  
  
 A continuación se muestra una breve descripción de los formularios para esta función:  
  
 **Format(** `pFormat` **)**  
 El valor usando la cadena de formato que contiene los códigos de formato especiales que van precedidos por un signo de porcentaje (%), da formato a este formulario como en `printf`. La cadena de formato se pasa como un parámetro a la función.  
  
 **Format(** `nID` **)**  
 El valor usando la cadena de formato que contiene los códigos de formato especiales que van precedidos por un signo de porcentaje (%), da formato a este formulario como en `printf`. La cadena de formato es un recurso. El identificador de este recurso de cadena se pasa como parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities&#15;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]  
  
##  <a name="getdays"></a>COleDateTimeSpan::GetDays  
 Recupera la parte de día de este valor de fecha o intervalo de tiempo.  
  
```
LONG GetDays() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La parte de día de este valor de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto aproximadamente: los valores de este intervalo de la función entre 3,615,000 y 3,615,000.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities Nº&16;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]  
  
##  <a name="gethours"></a>COleDateTimeSpan::GetHours  
 Recupera la parte de este valor de fecha o intervalo de tiempo.  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La parte de horas de este valor de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de la función entre-23 y 23.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
- [GetDays](#getdays)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities&#17;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]  
  
##  <a name="getminutes"></a>COleDateTimeSpan::GetMinutes  
 Recupera la parte de minutos de este valor de fecha o intervalo de tiempo.  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La parte de minutos de este valor de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de la función entre – 59 y 59.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities&#18;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]  
  
##  <a name="getseconds"></a>COleDateTimeSpan::GetSeconds  
 Recupera la segunda parte de este valor de fecha o intervalo de tiempo.  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La parte de segundos de este valor de fecha o intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de la función entre – 59 y 59.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities Nº&19;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]  
  
##  <a name="getstatus"></a>COleDateTimeSpan::GetStatus  
 Obtiene el estado (validez) de este `COleDateTimeSpan` objeto.  
  
```
DateTimeSpanStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de este `COleDateTimeSpan` valor.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto se define mediante la **DateTimeSpanStatus** tipo enumerado, que se define dentro de la `COleDateTimeSpan` clase.  
  
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleDateTimeSpan::valid** indica que este `COleDateTimeSpan` objeto es válido.  
  
- **COleDateTimeSpan::invalid** indica que este `COleDateTimeSpan` objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleDateTimeSpan::null** indica que este `COleDateTimeSpan` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
 El estado de un `COleDateTimeSpan` objeto no es válido en los casos siguientes:  
  
-   Si este objeto ha sufrido un desbordamiento o subdesbordamiento durante una operación aritmética de asignación, es decir, `+=` o `-=`.  
  
-   Si se asignó un valor no válido para este objeto.  
  
-   Si el estado de este objeto se estableció explícitamente en no válido con `SetStatus`.  
  
 Para obtener más información acerca de las operaciones que puede establecer el estado como no válida, consulte [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) y [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).  
  
 Para obtener más información acerca de los límites de `COleDateTimeSpan` valores, vea el artículo [fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays  
 Recupera este valor de fecha o intervalo de tiempo expresado en días.  
  
```
double GetTotalDays() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este valor de fecha o intervalo de tiempo expresado en días. Aunque esta función es devuelve un valor double, siempre devolverá un valor entero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de la función entre aproximadamente – 3.65e6 y 3.65e6.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities&#20;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]  
  
##  <a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours  
 Recupera este valor de fecha o intervalo de tiempo expresado en horas.  
  
```
double GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este valor de fecha o intervalo de tiempo expresado en horas. Aunque esta función es devuelve un valor double, siempre devolverá un valor entero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de la función entre aproximadamente – 8.77e7 y 8.77e7.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
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
 Recupera este valor de fecha o intervalo de tiempo expresado en minutos.  
  
```
double GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este valor de fecha o intervalo de tiempo expresado en minutos. Aunque esta función es devuelve un valor double, siempre devolverá un valor entero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos de este intervalo de la función entre aproximadamente – 5.26e9 y 5.26e9.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
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
 Este valor de fecha o intervalo de tiempo expresado en segundos. Aunque esta función es devuelve un valor double, siempre devolverá un valor entero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores devueltos por esta función oscilan entre aproximadamente: 3.16e11 a 3.16e11.  
  
 Para otras funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
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
 Subyacente **doble** valor `COleDateTime` objeto.  
  
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
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleDateTimeSpan::valid** indica que este `COleDateTimeSpan` objeto es válido.  
  
- **COleDateTimeSpan::invalid** indica que este `COleDateTimeSpan` objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleDateTimeSpan::null** indica que este `COleDateTimeSpan` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
 El estado de un `COleDateTimeSpan` objeto no es válido en los casos siguientes:  
  
-   Si este objeto ha sufrido un desbordamiento o subdesbordamiento durante una operación aritmética de asignación, es decir, `+=` o `-=`.  
  
-   Si se asignó un valor no válido para este objeto.  
  
-   Si el estado de este objeto se estableció explícitamente en no válido con [SetStatus](#setstatus).  
  
 Para obtener más información acerca de las operaciones que puede establecer el estado como no válida, consulte [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) y [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).  
  
> [!CAUTION]
>  Este miembro de datos es para situaciones de programación avanzadas. Debe utilizar las funciones de miembro insertada [GetStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para las precauciones adicionales con respecto a este miembro de datos se establece explícitamente.  
  
 Para obtener más información acerca de los límites de `COleDateTimeSpan` valores, vea el artículo [fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_eq"></a>COleDateTimeSpan::operator =  
 Copia un `COleDateTimeSpan` valor.  
  
```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este operador de asignación sobrecargado copia el valor de fecha o intervalo de tiempo de origen en esta `COleDateTimeSpan` objeto.  
  
##  <a name="operator_add_-"></a>COleDateTimeSpan::operator +, -  
 Agregar, restar y cambiar el signo de `COleDateTimeSpan` valores.  
  
```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Los dos primeros operadores permiten sumar y restar valores de fecha o intervalo de tiempo. La tercera le permite cambiar el signo de un valor de fecha o intervalo de tiempo.  
  
 Si cualquiera de los operandos es null, el estado del resultante `COleDateTimeSpan` valor es null.  
  
 Si cualquiera de los operandos es válido y el otro no es null, el estado del resultante `COleDateTimeSpan` valor no es válido.  
  
 Para obtener más información sobre los valores de estado válido, null y no válidos, consulte el [m_status](#m_status) variable miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_ATLMFC_Utilities #](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator +=, =  
 Sumar y restar un `COleDateTimeSpan` el valor de este `COleDateTimeSpan` valor.  
  
```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Estos operadores permiten sumar y restar valores de intervalo de fecha/tiempo de esta `COleDateTimeSpan` objeto. Si cualquiera de los operandos es null, el estado del resultante `COleDateTimeSpan` valor es null.  
  
 Si cualquiera de los operandos es válido y el otro no es null, el estado del resultante `COleDateTimeSpan` valor no es válido.  
  
 Para obtener más información sobre los valores de estado válido, null y no válidos, consulte el [m_status](#m_status) variable miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities&#24;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]  
  
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
 Indique los valores de intervalo de fechas y el intervalo de tiempo que se copiará en este `COleDateTimeSpan` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para las funciones que consultar el valor de un `COleDateTimeSpan` de objeto, vea las siguientes funciones miembro:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_ATLMFC_Utilities](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]  
  
##  <a name="setstatus"></a>COleDateTimeSpan::SetStatus  
 Establece el estado (validez) de este `COleDateTimeSpan` objeto.  
  
```
void SetStatus(DateTimeSpanStatus status) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *status*  
 El nuevo valor para este `COleDateTimeSpan` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El *estado* el valor del parámetro se define mediante la **DateTimeSpanStatus** tipo enumerado, que se define dentro de la `COleDateTimeSpan` clase.  
  
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleDateTimeSpan::valid** indica que este `COleDateTimeSpan` objeto es válido.  
  
- **COleDateTimeSpan::invalid** indica que este `COleDateTimeSpan` objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleDateTimeSpan::null** indica que este `COleDateTimeSpan` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
    > [!CAUTION]
    >  Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Frecuentemente se utilizará para establecer el estado `null` o **válido**. Tenga en cuenta que el operador de asignación ( [operador =](#eq)) y [SetDateTimeSpan](#setdatetimespan) establecer el estado del objeto basado en los valores de origen.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities&#22;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [COleDateTime (clase)](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime (clase)](../../atl-mfc-shared/reference/ctime-class.md)   
 [Clase CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)



