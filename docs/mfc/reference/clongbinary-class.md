---
title: CLongBinary (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BLOB
- CLongBinary
dev_langs:
- C++
helpviewer_keywords:
- BLOB (binary large object)
- CLongBinary class
- BLOB (binary large object), CLongBinary class
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
caps.latest.revision: 21
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: bb73604ee4d15f3a71be8514f348ad265064928a
ms.lasthandoff: 02/24/2017

---
# <a name="clongbinary-class"></a>CLongBinary (clase)
Simplifica el trabajo con objetos de datos binarios de gran tamaño (a menudo denominados BLOB, u "objetos binarios grandes") en una base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CLongBinary : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CLongBinary::CLongBinary](#clongbinary)|Construye un objeto `CLongBinary`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Contiene el tamaño real en bytes del objeto de datos cuyo identificador se almacena en `m_hData`.|  
|[CLongBinary::m_hData](#m_hdata)|Contiene un Windows `HGLOBAL` identificador del objeto de imagen real.|  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, un campo de registro en una tabla SQL puede contener un mapa de bits que representa una imagen. Un `CLongBinary` objeto almacena este tipo de objeto y realiza un seguimiento de su tamaño.  
  
> [!NOTE]
>  En general, es mejor práctica ahora usar [CByteArray](../../mfc/reference/cbytearray-class.md) junto con el [DFX_Binary](http://msdn.microsoft.com/library/678021a3-2e46-44d7-8528-71bb692dcc07) (función). Todavía puede usar `CLongBinary`, pero en general `CByteArray` proporciona más funcionalidad en Win32, puesto que ya no hay la limitación de tamaño que se encuentra con 16 bits `CByteArray`. Este Consejo se aplica a la programación con objetos de acceso a datos (DAO), así como Open Database Connectivity (ODBC).  
  
 Para usar un `CLongBinary` objeto, declarar un miembro de datos de campo de tipo `CLongBinary` en la clase de conjunto de registros. Este miembro será un miembro de la clase de conjunto de registros incrustado y se construirá cuando se construye el conjunto de registros. Después de la `CLongBinary` se construye el objeto, el mecanismo de campos de registros (RFX) de exchange, carga el objeto de datos de un campo en el registro actual en el origen de datos y almacena hacia el registro cuando se actualiza el registro. RFX consulta el origen de datos para el tamaño del objeto binario grande, le asigna almacenamiento (a través de la `CLongBinary` del objeto `m_hData` miembro de datos) y almacena una `HGLOBAL` identificador de los datos de `m_hData`. RFX también almacena el tamaño real del objeto de datos en el `m_dwDataLength` miembro de datos. Trabajar con los datos en el objeto a través de `m_hData`, utilizando las mismas técnicas que normalmente se utilizan para manipular los datos almacenados en un Windows `HGLOBAL` controlar.  
  
 Cuando se destruya el conjunto de registros, el objeto incrustado `CLongBinary` también se destruye el objeto y su destructor desasigna el `HGLOBAL` identificador de datos.  
  
 Para obtener más información acerca de objetos grandes y el uso de `CLongBinary`, consulte los artículos [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md) y [conjunto de registros: trabajar con elementos grandes de datos (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb_.h  
  
##  <a name="a-nameclongbinarya--clongbinaryclongbinary"></a><a name="clongbinary"></a>CLongBinary::CLongBinary  
 Construye un objeto `CLongBinary`.  
  
```  
CLongBinary();
```  
  
##  <a name="a-namemdwdatalengtha--clongbinarymdwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength  
 Almacena el tamaño real en bytes de los datos almacenados en el `HGLOBAL` controlar en `m_hData`.  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este tamaño puede ser menor que el tamaño del bloque de memoria asignado para los datos. Llamar a Win32 [GLobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593) función para obtener el tamaño asignado.  
  
##  <a name="a-namemhdataa--clongbinarymhdata"></a><a name="m_hdata"></a>CLongBinary::m_hData  
 Almacena un Windows `HGLOBAL` tratar a los datos reales de objetos binarios grandes.  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)

