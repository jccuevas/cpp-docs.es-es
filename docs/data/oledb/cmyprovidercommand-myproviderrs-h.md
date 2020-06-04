---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- ccustomcommand
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: afa8571173117a23962eb84f6fa5b4cf2c3c46e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211762"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

La clase `CCustomCommand` es la implementación del objeto de comando de proveedor. Proporciona la implementación de las interfaces `IAccessor`, `ICommandText`y `ICommandProperties`. La interfaz `IAccessor` es la misma que la del conjunto de filas. El objeto Command usa el descriptor de acceso para especificar enlaces para los parámetros. El objeto Rowset los utiliza para especificar enlaces para las columnas de salida. La interfaz de `ICommandText` es una manera útil de especificar un comando textualmente. En este ejemplo se usa la interfaz `ICommandText` posteriormente cuando agrega código personalizado. también invalida el método `ICommand::Execute`. La interfaz `ICommandProperties` controla todas las propiedades de los objetos de comando y conjunto de filas.

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

La interfaz de `IAccessor` administra todos los enlaces utilizados en comandos y conjuntos de filas. El consumidor llama a `IAccessor::CreateAccessor` con una matriz de estructuras de `DBBINDING`. Cada estructura de `DBBINDING` contiene la información sobre cómo se deben controlar los enlaces de columna (por ejemplo, el tipo y la longitud). El proveedor recibe las estructuras y, a continuación, determina cómo se deben transferir los datos y si es necesaria alguna conversión. La interfaz de `IAccessor` se usa en el objeto de comando para controlar los parámetros en el comando.

El objeto de comando también proporciona una implementación de `IColumnsInfo`. OLE DB requiere la interfaz `IColumnsInfo`. La interfaz permite al consumidor recuperar información acerca de los parámetros del comando. El objeto Rowset utiliza la interfaz `IColumnsInfo` para devolver información sobre las columnas de salida al proveedor.

El proveedor también contiene una interfaz denominada `IObjectWithSite`. La interfaz de `IObjectWithSite` se implementó en ATL 2,0 y permite que el implementador pase información sobre sí misma a su elemento secundario. El objeto Command utiliza la información de `IObjectWithSite` para indicar a los objetos de conjunto de filas generados sobre quién los creó.

## <a name="see-also"></a>Consulte también

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)
