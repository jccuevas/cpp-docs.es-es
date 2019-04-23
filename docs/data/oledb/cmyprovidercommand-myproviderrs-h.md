---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
- ccustomcommand
- customrs.h
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: b10d7bccae6fa9b86d072b8e13791f23516b2c63
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028566"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

La `CCustomCommand` clase es la implementación para el objeto de comando del proveedor. Proporciona la implementación para el `IAccessor`, `ICommandText`, y `ICommandProperties` interfaces. El `IAccessor` interfaz es el mismo que del conjunto de filas. El objeto de comando utiliza el descriptor de acceso para especificar enlaces de parámetros. El objeto de conjunto de filas utiliza para especificar enlaces para las columnas de salida. El `ICommandText` interfaz es una forma útil para especificar un comando textualmente. Este ejemplo se usa el `ICommandText` interfaz más adelante, cuando agrega código personalizado; también invalida la `ICommand::Execute` método. El `ICommandProperties` interfaz controla todas las propiedades de los objetos de comando y conjunto de filas.

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

El `IAccessor` interfaz administra todos los enlaces utilizados en comandos y conjuntos de filas. El consumidor llama a `IAccessor::CreateAccessor` con una matriz de `DBBINDING` estructuras. Cada `DBBINDING` estructura contiene información sobre cómo deben controlarse los enlaces de columna (por ejemplo, tipo y longitud). El proveedor recibe las estructuras y, a continuación, determina cómo se deben transferir los datos y si es necesaria ninguna conversión. El `IAccessor` interfaz se utiliza en el objeto de comando para controlar los parámetros en el comando.

El objeto de comando también proporciona una implementación de `IColumnsInfo`. OLE DB requiere el `IColumnsInfo` interfaz. La interfaz permite al consumidor recuperar información acerca de los parámetros del comando. El objeto de conjunto de filas utiliza el `IColumnsInfo` interfaz para devolver información acerca de las columnas de salida para el proveedor.

El proveedor también contiene una interfaz denominada `IObjectWithSite`. El `IObjectWithSite` interfaz se implementó en ATL 2.0 y permite al implementador pasar información sobre sí mismo a su elemento secundario. El objeto de comando utiliza el `IObjectWithSite` información para indicar a cualquiera genera objetos de conjunto de filas que los creó.

## <a name="see-also"></a>Vea también

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)