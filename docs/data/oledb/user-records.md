---
title: Registros de usuario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_MAP
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aea6b4b2ebb1a02e4ef669b437fbe7eb30937f9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="user-records"></a>Registros de usuario
Para usar un descriptor de acceso estática (es decir, un descriptor de acceso se deriva de **CAccessor)**, el consumidor debe poseer un registro de usuario. El registro de usuario es una clase de C++ que contiene elementos de datos que controlan la entrada o salida. El Asistente para consumidores OLE DB ATL genera un registro de usuario para el consumidor. Puede agregar métodos para el registro de usuario para realizar tareas opcionales como control de comandos.  
  
 El código siguiente muestra un registro de ejemplo que controla los comandos. En el registro de usuario, `BEGIN_COLUMN_MAP` representa un conjunto de filas de datos pasado al consumidor desde un proveedor. `BEGIN_PARAM_MAP` Representa un conjunto de parámetros del comando. Este ejemplo se utiliza un [CCommand](../../data/oledb/ccommand-class.md) clase para administrar los parámetros del comando. Los miembros de datos en las entradas del mapa representan desplazamientos en un bloque contiguo de memoria para cada instancia de la clase. El `COLUMN_ENTRY` macros corresponden a la `PROVIDER_COLUMN_ENTRY` macros en el lado del proveedor.  
  
 Para obtener más información sobre la **COLUMN_MAP** y **PARAM_MAP** macros, consulte [Macros para plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
```  
class CArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_COLUMN_MAP(CArtists)  
   COLUMN_ENTRY(1, m_szFirstName)  
   COLUMN_ENTRY(2, m_szLastName)  
   COLUMN_ENTRY(3, m_nAge)  
END_COLUMN_MAP()  
  
// Parameter binding map  
BEGIN_PARAM_MAP(CArtists)  
   COLUMN_ENTRY(1, m_nAge)  
END_PARAM_MAP()  
};  
```  
  
## <a name="wizard-generated-user-records"></a>Registros de usuario generados por el Asistente  
 Si utiliza al Asistente para consumidores OLE DB ATL para generar un consumidor, tiene la opción de utilizar plantillas OLE DB o atributos OLE DB. El código generado es diferente en cada caso. Para obtener más información acerca de este código, consulte [clases generadas](../../data/oledb/consumer-wizard-generated-classes.md).  
  
## <a name="user-record-support-for-multiple-accessors"></a>Compatibilidad con registros de usuario de varios descriptores de acceso  
 Para obtener una explicación detallada de los escenarios en los que es necesario utilizar varios descriptores de acceso, consulte [utilizar varios descriptores de acceso en un conjunto de filas](../../data/oledb/using-multiple-accessors-on-a-rowset.md).  
  
 En el ejemplo siguiente se muestra el registro de usuario modificado para admitir varios descriptores de acceso en el conjunto de filas. En lugar de `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP`, usa [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) y [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) para cada descriptor de acceso. El `BEGIN_ACCESSOR` macro especifica el número de descriptor de acceso (desplazamiento respecto a cero) y si el descriptor de acceso es autoaccessor. Llamada de Autoaccessors `GetData` para recuperar datos automáticamente en una llamada a [MoveNext](../../data/oledb/crowset-movenext.md). Descriptores de acceso debe recuperar los datos de forma explícita. Utilice un descriptor de acceso si va a enlazar a un campo de datos de gran tamaño (por ejemplo, una imagen de mapa de bits) que no puede recuperar para todos los registros.  
  
```  
class CMultiArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)  
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor  
    COLUMN_ENTRY(1, m_szFirstName)  
    COLUMN_ENTRY(2, m_szLastName)  
   END_ACCESSOR()  
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor  
    COLUMN_ENTRY(3, m_nAge)  
   END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)