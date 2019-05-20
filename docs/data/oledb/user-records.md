---
title: Registros de usuario
ms.date: 05/09/2019
f1_keywords:
- COLUMN_ENTRY_MAP
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
ms.openlocfilehash: c9c1126f0e8248f31ac739bb1d939f811bda678d
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525285"
---
# <a name="user-records"></a>Registros de usuario

> [!NOTE]
> El Asistente para consumidores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores. Puede seguir agregando la funcionalidad manualmente. Para obtener más información, consulte [Crear un consumidor sin utilizar un asistente](creating-a-consumer-without-using-a-wizard.md).

Para usar un descriptor de acceso estático (es decir, se deriva un descriptor de acceso de `CAccessor`), el consumidor debe tener un registro de usuario. El registro de usuario es una clase C++ que contiene los elementos de datos que controlan la entrada o salida. El **Asistente para consumidores OLE DB ATL** genera un registro de usuario para el consumidor. Puede agregar métodos al registro de usuario para realizar tareas opcionales como el control de comandos.

El código siguiente muestra un registro de ejemplo que controla los comandos. En el registro de usuario, BEGIN_COLUMN_MAP representa un conjunto de filas de datos pasado al consumidor de un proveedor. BEGIN_PARAM_MAP representa un conjunto de parámetros del comando. Este ejemplo se usa una clase [CCommand](../../data/oledb/ccommand-class.md) para controlar los parámetros del comando. Los miembros de datos en las entradas de asignación representan desplazamientos en un bloque contiguo de memoria para cada instancia de la clase. Las macros COLUMN_ENTRY corresponden a las macros PROVIDER_COLUMN_ENTRY en el lado del proveedor.

Para obtener más información sobre las macros COLUMN_MAP y PARAM_MAP, consulte [Macros for OLE DB Consumer Templates](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md) (Macros para olantillas de consumidor OLE DB).

```cpp
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

## <a name="wizard-generated-user-records"></a>Registros de usuario generados por el asistente

Si utiliza el **Asistente para consumidores OLE DB ATL** para generar un consumidor, tiene la opción de utilizar plantillas OLE DB o atributos OLE DB. El código generado es distinto en cada caso. Para obtener más información sobre este código, consulte [Clases generadas por el Asistente para consumidores](../../data/oledb/consumer-wizard-generated-classes.md).

## <a name="user-record-support-for-multiple-accessors"></a>Compatibilidad de los registros de usuario con varios descriptores de acceso

Para obtener una explicación detallada de los escenarios en los que es necesario utilizar varios descriptores de acceso, consulte [Utilizar varios descriptores de acceso en un conjunto de filas](../../data/oledb/using-multiple-accessors-on-a-rowset.md).

El ejemplo siguiente muestra el registro de usuario modificado para admitir varios descriptores de acceso en el conjunto de filas. En lugar de BEGIN_COLUMN_MAP y END_COLUMN_MAP, usa [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) y [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) para cada descriptor de acceso. La macro BEGIN_ACCESSOR especifica el número de descriptor de acceso (desplazamiento respecto a cero) y si el descriptor de acceso es descriptor de acceso automático. Los descriptores de acceso automático llaman a `GetData` para recuperar los datos automáticamente en una llamada a [MoveNext](../../data/oledb/crowset-movenext.md). Los descriptores de acceso requieren recuperar explícitamente los datos. Utilice un descriptor de acceso si desea enlazar a un campo de datos de gran tamaño (por ejemplo, una imagen de mapa de bits) que es posible que no desea recuperar para cada registro.

```cpp
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