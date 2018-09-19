---
title: CLongBinary (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
dev_langs:
- C++
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed0603482ffccf1bcb827d67b174768cfd3e3168
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196802"
---
# <a name="clongbinary-class"></a>CLongBinary (clase)
Simplifica el trabajo con objetos de datos binarios de gran tamaño (a menudo denominados BLOB, u "objetos binarios grandes") en una base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CLongBinary : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLongBinary::CLongBinary](#clongbinary)|Construye un objeto `CLongBinary`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Contiene el tamaño real en bytes del objeto de datos cuyo identificador se almacena en `m_hData`.|  
|[CLongBinary::m_hData](#m_hdata)|Contiene un identificador HGLOBAL de Windows para el objeto de imagen real.|  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, un campo de registro en una tabla SQL puede contener un mapa de bits que representa una imagen. Un `CLongBinary` almacena un objeto de este tipo de objeto y realiza un seguimiento de su tamaño.  
  
> [!NOTE]
>  En general, lo más recomendable es ahora usar [CByteArray](../../mfc/reference/cbytearray-class.md) junto con el [DFX_Binary](record-field-exchange-functions.md#dfx_binary) función. Todavía puede usar `CLongBinary`, pero en general `CByteArray` proporciona más funcionalidad en Win32, ya que no hay ya no lo está la limitación de tamaño encontrada con 16 bits `CByteArray`. Este Consejo se aplica a la programación con Data Access Objects (DAO), así como de Open Database Connectivity (ODBC).  
  
 Para usar un `CLongBinary` objeto, declare un miembro de datos de campo de tipo `CLongBinary` en la clase de conjunto de registros. Este miembro será un miembro incrustado de la clase de conjunto de registros y se generarán cuando se construye el conjunto de registros. Después de la `CLongBinary` se construye el objeto, el mecanismo de campos de registros (RFX) de exchange, carga el objeto de datos de un campo en el registro actual en el origen de datos y lo almacena hasta el registro cuando se actualiza el registro. RFX consulta el origen de datos para el tamaño de los objetos binarios grandes, asigna almacenamiento para ella (a través de la `CLongBinary` del objeto `m_hData` miembro de datos) y almacena una `HGLOBAL` controlar a los datos de `m_hData`. RFX también almacena el tamaño real del objeto de datos en el `m_dwDataLength` miembro de datos. Trabajar con los datos en el objeto a través de `m_hData`, utilizando las mismas técnicas que usaría normalmente para manipular los datos almacenados en un Windows `HGLOBAL` controlar.  
  
 Cuando se destruya el conjunto de registros, los datos incrustado `CLongBinary` también se destruye el objeto y su destructor se desasigna la `HGLOBAL` identificador de datos.  
  
 Para obtener más información acerca de los objetos grandes y el uso de `CLongBinary`, consulte los artículos [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md) y [conjunto de registros: trabajar con elementos de datos de gran tamaño (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb_.h  
  
##  <a name="clongbinary"></a>  CLongBinary::CLongBinary  
 Construye un objeto `CLongBinary`.  
  
```  
CLongBinary();
```  
  
##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength  
 Almacena el tamaño real en bytes de los datos almacenados en el identificador HGLOBAL en `m_hData`.  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este tamaño puede ser menor que el tamaño del bloque de memoria asignado para los datos. Llamar a Win32 [GLobalSize](/windows/desktop/api/winbase/nf-winbase-globalsize) función para obtener el tamaño asignado.  
  
##  <a name="m_hdata"></a>  CLongBinary::m_hData  
 Almacena un identificador HGLOBAL Windows a los datos reales de objetos binarios grandes.  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)
