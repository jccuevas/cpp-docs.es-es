---
title: Clase CFileTimeSpan | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileTimeSpan
- ATL.CFileTimeSpan
- ATL::CFileTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8a25bab65d9e5705a71eddde901e747c43a5a002
ms.lasthandoff: 02/24/2017

---
# <a name="cfiletimespan-class"></a>Clase CFileTimeSpan
Esta clase proporciona métodos para administrar asociados a un archivo de valores de hora y fecha relativa.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CFileTimeSpan
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Llamar a este método para recuperar el intervalo de tiempo desde la `CFileTimeSpan` objeto.|  
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Llamar a este método para establecer el intervalo de tiempo de la `CFileTimeSpan` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileTimeSpan::operator-](#operator_-)|Realiza la resta en una `CFileTimeSpan` objeto.|  
|[CFileTimeSpan::operator! =](#operator_neq)|Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.|  
|[CFileTimeSpan::operator +](#operator_add)|Realiza la adición de un `CFileTimeSpan` objeto.|  
|[CFileTimeSpan::operator +=](#operator_add_eq)|Realiza la adición de un `CFileTimeSpan` de objeto y asignar el resultado al objeto actual.|  
|[CFileTimeSpan::operator&lt;](#operator_lt)|Compara dos `CFileTimeSpan` objetos para determinar el menor.|  
|[CFileTimeSpan::operator&lt;=](#operator_lt_eq)|Compara dos `CFileTimeSpan` objetos para determinar la igualdad o inferior.|  
|[CFileTimeSpan::operator =](#operator_eq)|El operador de asignación.|  
|[CFileTimeSpan::operator =](#operator_-_eq)|Realiza la resta en una `CFileTimeSpan` de objeto y asignar el resultado al objeto actual.|  
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Compara dos objetos `CFileTimeSpan` para determinar si son iguales.|  
|[CFileTimeSpan::operator&gt;](#operator_gt)|Compara dos `CFileTimeSpan` objetos para determinar el mayor.|  
|[CFileTimeSpan::operator&gt;=](#operator_gt_eq)|Compara dos `CFileTimeSpan` objetos para determinar la igualdad o mayor.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para administrar relativos períodos de tiempo que se suelen encontrado al realizar operaciones relativas a un archivo se ha creado, el último acceso al o modificó por última vez. Los métodos de esta clase se utilizan con frecuencia junto con [CFileTime clase](../../atl-mfc-shared/reference/cfiletime-class.md) objetos.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atltime.h  
  
##  <a name="a-namecfiletimespana--cfiletimespancfiletimespan"></a><a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan  
 El constructor.  
  
```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan` existente.  
  
 `nSpan`  
 Un período de tiempo en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 El `CFileTimeSpan` objeto puede crearse mediante existente `CFileTimeSpan` de objeto o expresado como un valor de 64 bits. El constructor predeterminado establece el intervalo de tiempo en 0.  
  
##  <a name="a-namegettimespana--cfiletimespangettimespan"></a><a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan  
 Llamar a este método para recuperar el intervalo de tiempo desde la `CFileTimeSpan` objeto.  
  
```
LONGLONG GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el intervalo de tiempo en milisegundos.  
  
##  <a name="a-nameoperator-a--cfiletimespanoperator--"></a><a name="operator_-"></a>CFileTimeSpan::operator-  
 Realiza la resta en una **CFileTimeSpan** objeto.  
  
```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CFileTimeSpan` objeto que representa el resultado de la diferencia entre los dos intervalos de tiempo.  
  
##  <a name="a-nameoperatorneqa--cfiletimespanoperator-"></a><a name="operator_neq"></a>CFileTimeSpan::operator! =  
 Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.  
  
```
bool operator!=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si no es igual que el elemento está comparando el `CFileTimeSpan` objeto; en caso contrario **false**.  
  
##  <a name="a-nameoperatoradda--cfiletimespanoperator-"></a><a name="operator_add"></a>CFileTimeSpan::operator +  
 Realiza la adición de un `CFileTimeSpan` objeto.  
  
```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CFileTimeSpan` que contiene la suma de la hora de dos intervalos de objeto.  
  
##  <a name="a-nameoperatoraddeqa--cfiletimespanoperator-"></a><a name="operator_add_eq"></a>CFileTimeSpan::operator +=  
 Realiza la adición de un `CFileTimeSpan` de objetos y asigna el resultado al objeto actual.  
  
```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la actualización `CFileTimeSpan` que contiene la suma de la hora de dos intervalos de objeto.  
  
##  <a name="a-nameoperatorlta--cfiletimespanoperator-lt"></a><a name="operator_lt"></a>CFileTimeSpan::operator&lt;  
 Compara dos `CFileTimeSpan` objetos para determinar el menor.  
  
```
bool operator<(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el primer objeto es menor (es decir, representa un período de tiempo más corto) que el segundo, de lo contrario, **false**.  
  
##  <a name="a-nameoperatorlteqa--cfiletimespanoperator-lt"></a><a name="operator_lt_eq"></a>CFileTimeSpan::operator&lt;=  
 Compara dos `CFileTimeSpan` objetos para determinar la igualdad o inferior.  
  
```
bool operator<=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el primer objeto es menor que (es decir, representa un período de tiempo más corto) o igual que el segundo, de lo contrario, **false**.  
  
##  <a name="a-nameoperatoreqa--cfiletimespanoperator-"></a><a name="operator_eq"></a>CFileTimeSpan::operator =  
 El operador de asignación.  
  
```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CFileTimeSpan` objeto.  
  
##  <a name="a-nameoperator-eqa--cfiletimespanoperator--"></a><a name="operator_-_eq"></a>CFileTimeSpan::operator =  
 Realiza la resta en una `CFileTimeSpan` de objetos y asigna el resultado al objeto actual.  
  
```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CFileTimeSpan` objeto.  
  
##  <a name="a-nameoperatoreqeqa--cfiletimespanoperator-"></a><a name="operator_eq_eq"></a>CFileTimeSpan::operator ==  
 Compara dos objetos `CFileTimeSpan` para determinar si son iguales.  
  
```
bool operator==(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si los objetos son iguales; en caso contrario **false**.  
  
##  <a name="a-nameoperatorgta--cfiletimespanoperator-gt"></a><a name="operator_gt"></a>CFileTimeSpan::operator&gt;  
 Compara dos `CFileTimeSpan` objetos para determinar el mayor.  
  
```
bool operator>(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el primer objeto es mayor que (es decir, representa un período de tiempo) que el segundo, de lo contrario, **false**.  
  
##  <a name="a-nameoperatorgteqa--cfiletimespanoperator-gt"></a><a name="operator_gt_eq"></a>CFileTimeSpan::operator&gt;=  
 Compara dos `CFileTimeSpan` objetos para determinar la igualdad o mayor.  
  
```
bool operator>=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `span`  
 Objeto `CFileTimeSpan` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el primer objeto es mayor que (es decir, representa un período de tiempo) o igual que el segundo, de lo contrario, **false**.  
  
##  <a name="a-namesettimespana--cfiletimespansettimespan"></a><a name="settimespan"></a>CFileTimeSpan::SetTimeSpan  
 Llamar a este método para establecer el intervalo de tiempo de la `CFileTimeSpan` objeto.  
  
```
void SetTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nSpan`  
 El nuevo valor para el intervalo de tiempo en milisegundos.  
  
## <a name="see-also"></a>Vea también  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [Clase CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)



