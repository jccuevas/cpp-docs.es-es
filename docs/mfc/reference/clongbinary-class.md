---
title: "CLongBinary Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "BLOB"
  - "CLongBinary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB (objeto binario grande)"
  - "BLOB (objeto binario grande), CLongBinary (clase)"
  - "CLongBinary (clase)"
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLongBinary Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Simplifica trabajar con objetos de datos binarios de gran tamaño \(a menudo denominados BLOBs, o “objetos binarios grandes”\) en una base de datos.  
  
## Sintaxis  
  
```  
class CLongBinary : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLongBinary::CLongBinary](../Topic/CLongBinary::CLongBinary.md)|Crea un objeto `CLongBinary`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLongBinary::m\_dwDataLength](../Topic/CLongBinary::m_dwDataLength.md)|Contiene el tamaño real en bytes del objeto de datos cuyo identificador se almacena en `m_hData`.|  
|[CLongBinary::m\_hData](../Topic/CLongBinary::m_hData.md)|Contiene un identificador de Windows `HGLOBAL` al objeto real de la imagen.|  
  
## Comentarios  
 Por ejemplo, un campo de registro en una tabla SQL podría contener un mapa de bits que representa una imagen.  Un objeto de `CLongBinary` almacena por objeto y realizar un seguimiento de su tamaño.  
  
> [!NOTE]
>  Normalmente es un procedimiento recomendado utilizar ahora [CByteArray](../../mfc/reference/cbytearray-class.md) junto con la función de [DFX\_Binary](../Topic/DFX_Binary.md) .  Puede utilizar `CLongBinary`, pero en general `CByteArray` proporciona más funcionalidad en Win32, puesto que ya no existe la limitación de tamaño encontró con `CByteArray`de 16 bits.  Este consejos se refieren a la programación con Objetos de \(DAO\) acceso a datos con ODBC.  
  
 Para utilizar un objeto de `CLongBinary` , declarar un miembro de datos de campo de `CLongBinary` escrito en la clase de conjunto de registros.  Este miembro será miembro incrustado de la clase de conjunto de registros y se construido cuando se construya el conjunto de registros.  Después de que se cree el objeto de `CLongBinary` , el mecanismo de intercambio de campos de registros \(RFX\) carga el objeto de datos de un campo del registro actual en el origen de datos y lo almacena de nuevo en el registro cuando se actualice el registro.  Las consultas de RFX el origen de datos para el tamaño del objeto binario grande, asignan el almacenamiento para él \(a través del miembro de datos de `m_hData` del objeto de `CLongBinary` \), y almacena un identificador de `HGLOBAL` a los datos de `m_hData`.  RFX también almacena el tamaño real del objeto de datos en el miembro de datos de `m_dwDataLength` .  Ejecute los datos en el objeto con `m_hData`, utilizando las mismas técnicas que utilizaría normalmente para manipular los datos almacenados en un identificador de Windows `HGLOBAL` .  
  
 Cuando se destruye el conjunto de registros, el objeto incrustado de `CLongBinary` también se destruye, y su destructor desasigna el identificador de los datos de `HGLOBAL` .  
  
 Para obtener más información sobre objetos grandes y el uso de `CLongBinary`, vea los artículos [conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md) y [conjunto de registros: Trabajar con grandes elementos de datos \(ODBC\)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## Requisitos  
 **encabezado:** afxdb\_.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)