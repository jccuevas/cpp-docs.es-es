---
title: Plantillas de consumidor OLE DB (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- databases [C++], OLE DB templates
- OLE DB consumers [C++], data access
- OLE DB consumer templates [C++]
- databases [C++], consumers
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18bbcf64bc76d26535f9a5c2c51229048422af56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021582"
---
# <a name="ole-db-consumer-templates-c"></a>Plantillas de consumidor OLE DB (C++)

Las plantillas de consumidor OLE DB admiten la especificación de OLE DB versión 2.6. (Las plantillas de consumidor OLE DB se prueban en función de OLE DB 2.6, pero no son compatibles con todas las interfaces de la especificación). Las plantillas de consumidor reducen la cantidad de código que debe escribirse para implementar un consumidor OLE DB. Las plantillas proporcionan:  
  
- Acceso fácil a las características de OLE DB y una integración sin dificultad con ATL y MFC.  
  
- Un modelo de enlace sencillo para los parámetros y las columnas de la base de datos.  
  
- Tipos de datos nativos de C/C++ para la programación de OLE DB.  
  
Para usar las plantillas OLE DB, es necesario estar familiarizado con las plantillas de C++, COM y las interfaces OLE DB. Si no está familiarizado con OLE DB, consulte [referencia del programador de OLE DB](/previous-versions/windows/desktop/ms718124\(v=vs.85\)).  
  
Las plantillas OLE DB son compatibles con el modelo de objetos OLE DB existente en lugar de agregar un nuevo modelo de objetos. Las clases de nivel superior de las plantillas de consumidor OLE DB se corresponden con los componentes definidos en la especificación de OLE DB. El diseño de las plantillas de consumidor OLE DB incluye características avanzadas como, por ejemplo, varios descriptores de acceso en un conjunto de filas. El uso de plantillas y herencia múltiple permite que la biblioteca mantenga su flexibilidad y un tamaño reducido.  
  
## <a name="how-ole-db-consumers-access-data"></a>Cómo acceden los consumidores OLE DB a los datos  

Los consumidores usan diferentes tipos de objetos, que se describen en los temas siguientes:  
  
- [Orígenes de datos y sesiones](../../data/oledb/data-sources-and-sessions.md)  
  
- [Descriptores de acceso y conjuntos de filas](../../data/oledb/accessors-and-rowsets.md)  
  
- [Comandos y tablas](../../data/oledb/commands-and-tables.md)  
  
- [Registros de usuario](../../data/oledb/user-records.md)  
  
Antes de que el consumidor haga nada, primero seleccione un proveedor OLE DB adecuado para el tipo de base de datos que al que desea tener acceso (por ejemplo, SQL, Oracle, ODBC y MSDS). Para ello, se suele usar un enumerador (vea [CEnumerator](../../data/oledb/cenumerator-class.md) como se mencionó en [Orígenes de datos y sesiones](../../data/oledb/data-sources-and-sessions.md)).  
  
El [objeto de origen de datos](../../data/oledb/data-sources-and-sessions.md) proporciona la información de conexión necesaria para conectarse al origen de datos seleccionado. El objeto de origen de datos también contiene información de autenticación (por ejemplo, nombres de inicio de sesión y contraseñas), que se usa para permitir a los usuarios el acceso al origen de datos. El objeto de origen de datos establece una conexión con la base de datos y luego crea uno o varios objetos de sesión. Cada [objeto de sesión](../../data/oledb/data-sources-and-sessions.md) controla su propia interacción con la base de datos (es decir, consultar y recuperar datos) y realiza estas transacciones independientemente de las demás sesiones existentes.  
  
La sesión crea los objetos de comando y de conjunto de filas. El [objeto de comando](../../data/oledb/commands-and-tables.md) permite a los usuarios interactuar con la base de datos; por ejemplo, mediante comandos SQL. El [objeto de conjunto de filas](../../data/oledb/accessors-and-rowsets.md) es un conjunto de datos por el que es posible navegar y en el que se pueden [actualizar, eliminar e insertar filas](../../data/oledb/updating-rowsets.md).  
  
Un consumidor OLE DB enlaza las columnas de las tablas de la base de datos con variables locales. Para ello, usa un [descriptor de acceso](../../data/oledb/accessors-and-rowsets.md), que contiene un mapa que indica cómo se almacenan los datos en el consumidor. El mapa se compone de un conjunto de enlaces entre las columnas de la tabla y los búferes locales (variables) de la aplicación de consumidor.  
  
Un concepto importante cuando se trabaja con consumidores es declarar dos clases en el consumidor: la [clase de comando (o tabla)](../../data/oledb/commands-and-tables.md) y la [clase de registro de usuario](../../data/oledb/user-records.md). Es posible acceder a los conjuntos de filas a través de la clase de comando (o tabla), que se hereda de una clase de descriptor de acceso y una clase de conjunto de filas. La clase de registro de usuario contiene el mapa de enlaces de conjunto de filas descrito anteriormente.  
  
Para obtener más información, vea los temas siguientes:  
  
- [Crear un consumidor OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)  
  
- [Escenarios comunes de consumidor OLE DB (ejemplos)](../../data/oledb/working-with-ole-db-consumer-templates.md)  
  
## <a name="see-also"></a>Vea también  

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Acceso a datos](../data-access-in-cpp.md)<br/>
[Documentación del SDK de OLE DB](/previous-versions/windows/desktop/ms722784\(v=vs.85\))   
[Referencia del programador OLE DB](/previous-versions/windows/desktop/ms713643\(v=vs.85\))