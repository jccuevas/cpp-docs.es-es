---
title: "Registros de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "descriptores de acceso [C++], conjuntos de filas"
  - "descriptores de acceso [C++], static"
  - "BEGIN_ACCESSOR (macro), ejemplo"
  - "BEGIN_ACCESSOR_MAP (macro)"
  - "CAccessor (clase), ejemplo"
  - "COLUMN_ENTRY (macro)"
  - "COLUMN_ENTRY_MAP (macro)"
  - "plantillas de consumidor OLE DB, registros de usuario"
  - "conjuntos de filas [C++], descriptores de acceso"
  - "registros de usuario, plantillas de consumidor OLE DB"
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Registros de usuario
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para usar un descriptor de acceso estático, es decir, derivado de **CAccessor\)**, el consumidor debe poseer un registro de usuario.  El registro de usuario es una clase de C\+\+ que contiene elementos de datos que controlan la entrada o salida.  El Asistente para consumidores OLE DB ATL genera un registro de usuario para nuestro consumidor.  Se pueden agregar métodos al registro para realizar tareas opcionales como el control de comandos.  
  
 El código siguiente muestra un registro de ejemplo que controla la ejecución de comandos.  En el registro de usuario, `BEGIN_COLUMN_MAP` representa un conjunto de filas de datos pasado al consumidor desde un proveedor.  `BEGIN_PARAM_MAP` representa un conjunto de parámetros de comando.  En este ejemplo se usa una clase [CCommand](../../data/oledb/ccommand-class.md) para controlar los parámetros de comando.  Los miembros de datos de las entradas de mapa representan posiciones de desplazamiento en un bloque contiguo de memoria por cada instancia de la clase.  Las macros `COLUMN_ENTRY` corresponden a las macros `PROVIDER_COLUMN_ENTRY` del lado del proveedor.  
  
 Para obtener más información acerca de las macros **COLUMN\_MAP** y **PARAM\_MAP**, vea [Macros para plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
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
  
## Registros de usuario generados por el asistente  
 Si se utiliza el Asistente para consumidores OLE DB ATL para generar un consumidor, se puede elegir entre el uso de plantillas OLE DB o atributos OLE DB.  En función de la elección, el código generado es diferente.  Para obtener más información acerca del código, vea [Clases generadas por el Asistente para consumidores](../../data/oledb/consumer-wizard-generated-classes.md).  
  
## Compatibilidad del registro de usuario con múltiples descriptores de acceso  
 Para obtener información detallada de los escenarios en que es necesario utilizar múltiples descriptores de acceso, vea [Utilizar varios descriptores de acceso en un conjunto de filas](../../data/oledb/using-multiple-accessors-on-a-rowset.md).  
  
 El ejemplo siguiente muestra el registro de usuario modificado para que admita múltiples descriptores de acceso en el conjunto de filas.  En lugar de `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP`, se utiliza [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md) y [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) para cada descriptor de acceso.  La macro `BEGIN_ACCESSOR` especifica el número de descriptor de acceso \(desplazamiento respecto a cero\) y si el descriptor de acceso es del tipo automático \(autoaccessor\).  Los descriptores de acceso automáticos llaman a `GetData` para recuperar datos automáticamente en una llamada a [MoveNext](../../data/oledb/crowset-movenext.md).  Los descriptores de acceso no automáticos requieren recuperar explícitamente los datos.  Utilice un descriptor de acceso no automático si crea un enlace con un gran campo de datos \(como un mapa de bits\) que no desea recuperar en cada registro.  
  
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
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)