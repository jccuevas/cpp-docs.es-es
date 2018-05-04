---
title: Clase CFileTime | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
dev_langs:
- C++
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92acaa02ada550f1a2dcbf33a0e0e67b88347a5d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cfiletime-class"></a>Clase CFileTime
Esta clase proporciona métodos para administrar los valores de fecha y hora asociados a un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CFileTime :  public FILETIME
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTime::CFileTime](#cfiletime)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTime::GetCurrentTime](#getcurrenttime)|Llame a esta función estática para recuperar un `CFileTime` objeto que representa la fecha actual del sistema y la hora.|  
|[CFileTime::GetTime](#gettime)|Llamar a este método para recuperar la hora de la `CFileTime` objeto.|  
|[CFileTime::LocalToUTC](#localtoutc)|Llame a este método para convertir una hora de archivo local en una hora de archivo basada en la hora Universal coordinada (UTC).|  
|[CFileTime::SetTime](#settime)|Llamar a este método para establecer la fecha y hora almacenados por la `CFileTime` objeto.|  
|[CFileTime::UTCToLocal](#utctolocal)|Llame a este método para convertir la hora que se basa en la hora Universal coordinada (UTC) a la hora de archivo local.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTime::operator-](#operator_-)|Este operador se utiliza para restar en un `CFileTime` o `CFileTimeSpan` objeto.|  
|[CFileTime::operator! =](#operator_neq)|Este operador compara dos `CFileTime` objetos no son iguales.|  
|[CFileTime::operator +](#operator_add)|Este operador se usa para sumar en un objeto `CFileTimeSpan`.|  
|[CFileTime::operator +=](#operator_add_eq)|Este operador se usa para sumar en un objeto `CFileTimeSpan` y asignar el resultado al objeto actual.|  
|[CFileTime::operator &lt;](#operator_lt)|Este operador compara dos objetos `CFileTime` para determinar el menor.|  
|[CFileTime::operator &lt;=](#operator_lt_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el menor.|  
|[CFileTime::operator =](#operator_eq)|El operador de asignación.|  
|[CFileTime::operator =](#operator_-_eq)|Este operador se utiliza para restar en un `CFileTimeSpan` de objetos y asignar el resultado al objeto actual.|  
|[CFileTime::operator ==](#operator_eq_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales.|  
|[CFileTime::operator &gt;](#operator_gt)|Este operador compara dos objetos `CFileTime` para determinar el mayor.|  
|[CFileTime::operator &gt;=](#operator_gt_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el mayor.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CFileTime::Day](#day)|Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen un día.|  
|[CFileTime::Hour](#hour)|Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen una hora.|  
|[CFileTime::Millisecond](#millisecond)|Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen un milisegundo.|  
|[CFileTime::Minute](#minute)|Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen un minuto.|  
|[CFileTime::Second](#second)|Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen un segundo.|  
|[CFileTime::Week](#week)|Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen una semana.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para administrar los valores de fecha y hora asociados a la creación, acceso y modificación de archivos. Los métodos y datos de esta clase se suelen usar en conjunción con `CFileTimeSpan` objetos, que tratan con valores de tiempo relativos.  
  
 El valor de fecha y hora se almacena como un valor de 64 bits que representa el número de intervalos de 100 nanosegundos desde el 1 de enero de 1601. Este es el formato de hora Universal coordinada (UTC).  
  
 Las siguientes variables de miembro constantes estáticos se proporcionan para simplificar los cálculos:  
  
|Variable de miembro|Número de intervalos de 100 nanosegundos|  
|---------------------|-----------------------------------------|  
|Millisecond|10,000|  
|Second|Milisegundo * 1000|  
|Minute|Segundo * 60|  
|Hour|Minutos * 60|  
|Day|Hora * 24|  
|Semana|Día * 7|  
  
 **Tenga en cuenta** no todos los sistemas de archivos pueden registrar la creación y la hora del último acceso y no todos los sistemas de archivos grabarlos en la misma manera. Por ejemplo, en el sistema de archivos FAT de Windows NT, cree tiempo tiene una resolución de 10 milisegundos, tiempo de escritura con una resolución de 2 segundos y hora de acceso tenga una resolución de 1 día (fecha de acceso). En NTFS, hora de acceso tenga una resolución de 1 hora. Además, FAT registra veces en el disco en la hora local, pero NTFS registros veces en el disco en formato UTC. Para obtener más información, consulte [los tiempos de archivos](http://msdn.microsoft.com/library/windows/desktop/ms724290).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `FILETIME`  
  
 `CFileTime`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atltime.h  
  
##  <a name="cfiletime"></a>  CFileTime::CFileTime  
 El constructor.  
  
```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ft`  
 A [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) estructura.  
  
 `nTime`  
 La fecha y hora expresadas como un valor de 64 bits.  
  
### <a name="remarks"></a>Comentarios  
 El `CFileTime` objeto puede crearse con una fecha existente y la hora de un `FILETIME` estructura o expresado como un valor de 64 bits (en local o formatos de hora de la hora Universal coordinada (UTC)). El constructor predeterminado establece el tiempo en 0.  
  
##  <a name="day"></a>  CFileTime::Day  
 Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen un día.  
  
```
static const ULONGLONG Day = Hour* 24;
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFileTime::Millisecond](#millisecond).  
  
##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime  
 Llame a esta función estática para recuperar un `CFileTime` objeto que representa la fecha actual del sistema y la hora.  
  
```
static CFileTime GetCurrentTime() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la fecha actual del sistema y la hora en formato de hora Universal coordinada (UTC).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]  
  
##  <a name="gettime"></a>  CFileTime::GetTime  
 Llamar a este método para recuperar la hora de la `CFileTime` objeto.  
  
```
ULONGLONG GetTime() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la fecha y hora como un número de 64 bits, que puede estar en local o en formato de hora Universal coordinada (UTC).  
  
##  <a name="hour"></a>  CFileTime::Hour  
 Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen una hora.  
  
```
static const ULONGLONG Hour = Minute* 60;
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFileTime::Millisecond](#millisecond).  
  
##  <a name="localtoutc"></a>  CFileTime::LocalToUTC  
 Llame a este método para convertir una hora de archivo local en una hora de archivo basada en la hora Universal coordinada (UTC).  
  
```
CFileTime LocalToUTC() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CFileTime` objeto que contiene la hora en formato UTC.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFileTime::UTCToLocal](#utctolocal).  
  
##  <a name="millisecond"></a>  CFileTime::Millisecond  
 Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen un milisegundo.  
  
```
static const ULONGLONG Millisecond = 10000;
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]  
  
##  <a name="minute"></a>  CFileTime::Minute  
 Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen un minuto.  
  
```
static const ULONGLONG Minute = Second* 60;
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFileTime::Millisecond](#millisecond).  
  
##  <a name="operator_-"></a>  CFileTime::operator-  
 Este operador se utiliza para restar en un `CFileTime` o `CFileTimeSpan` objeto.  
  
```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Un objeto `CFileTimeSpan`.  
  
 `ft`  
 Un objeto `CFileTime`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CFileTime` objeto o un `CFileTimeSpan` objeto que representa el resultado de la diferencia horaria entre los dos objetos.  
  
##  <a name="operator_neq"></a>  CFileTime::operator! =  
 Este operador compara dos `CFileTime` objetos no son iguales.  
  
```
bool operator!=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ft`  
 Objeto `CFileTime` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si no es igual que el elemento que se están comparando el `CFileTime` objeto, en caso contrario **false**.  
  
##  <a name="operator_add"></a>  CFileTime::operator +  
 Este operador se usa para sumar en un objeto `CFileTimeSpan`.  
  
```
CFileTime operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Un objeto `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CFileTime` objeto que representa el resultado de la hora original más un tiempo relativo.  
  
##  <a name="operator_add_eq"></a>  CFileTime::operator +=  
 Este operador se usa para sumar en un objeto `CFileTimeSpan` y asignar el resultado al objeto actual.  
  
```
CFileTime& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Un objeto `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la actualización `CFileTime` objeto, que representa el resultado de la hora original más una hora relativa.  
  
##  <a name="operator_lt"></a>  CFileTime::operator &lt;  
 Este operador compara dos objetos `CFileTime` para determinar el menor.  
  
```
bool operator<(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ft`  
 Objeto `CFileTime` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el primer objeto es menor (anteriormente en el tiempo) que el segundo, **false** en caso contrario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]  
  
##  <a name="operator_lt_eq"></a>  CFileTime::operator &lt;=  
 Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el menor.  
  
```
bool operator<=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ft`  
 Objeto `CFileTime` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el primer objeto es menor que (más adelante en el tiempo) o igual que el segundo, en caso contrario, **false**.  
  
##  <a name="operator_eq"></a>  CFileTime::operator =  
 El operador de asignación.  
  
```
CFileTime& operator=(const FILETIME& ft) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ft`  
 Un `CFileTime` objeto que contiene la fecha y hora nuevas.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la actualización `CFileTime` objeto.  
  
##  <a name="operator_-_eq"></a>  CFileTime::operator =  
 Este operador se utiliza para restar en un `CFileTimeSpan` de objetos y asignar el resultado al objeto actual.  
  
```
CFileTime& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Un `CFileTimeSpan` que contiene la hora relativa a restar del objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la actualización `CFileTime` objeto.  
  
##  <a name="operator_eq_eq"></a>  CFileTime::operator ==  
 Este operador compara dos objetos `CFileTime` para determinar si son iguales.  
  
```
bool operator==(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ft`  
 La `CFileTime` objeto que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si los objetos son iguales, de lo contrario, **false**.  
  
##  <a name="operator_gt"></a>  CFileTime::operator &gt;  
 Este operador compara dos objetos `CFileTime` para determinar el mayor.  
  
```
bool operator>(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ft`  
 Objeto `CFileTime` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el primer objeto es mayor que (más adelante en el tiempo) que el segundo, en caso contrario, **false**.  
  
##  <a name="operator_gt_eq"></a>  CFileTime::operator &gt;=  
 Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el mayor.  
  
```
bool operator>=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ft`  
 Objeto `CFileTime` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el primer objeto es mayor que (más adelante en el tiempo) o igual que el segundo, en caso contrario, **false**.  
  
##  <a name="second"></a>  CFileTime::Second  
 Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen un día.  
  
```
static const ULONGLONG Second = Millisecond* 1000;
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFileTime::Millisecond](#millisecond).  
  
##  <a name="settime"></a>  CFileTime::SetTime  
 Llamar a este método para establecer la fecha y hora almacenados por la `CFileTime` objeto.  
  
```
void SetTime(ULONGLONG nTime) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nTime`  
 El valor de 64 bits que representa la fecha y hora, en formato de hora Universal coordinada (UTC) o local.  
  
##  <a name="utctolocal"></a>  CFileTime::UTCToLocal  
 Llame a este método para convertir la hora que se basa en la hora Universal coordinada (UTC) a la hora de archivo local.  
  
```
CFileTime UTCToLocal() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CFileTime` objeto que contiene la hora en formato de hora de archivo local.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]  
  
##  <a name="week"></a>  CFileTime::Week  
 Un miembro de datos estático que se almacena el número de intervalos de 100 nanosegundos que componen una semana.  
  
```
static const ULONGLONG Week = Day* 7;
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFileTime::Millisecond](#millisecond).  
  
## <a name="see-also"></a>Vea también  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [Clase CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


