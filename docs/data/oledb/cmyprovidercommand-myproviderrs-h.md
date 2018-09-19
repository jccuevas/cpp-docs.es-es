---
title: CMyProviderCommand (MyProviderRS.H) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 919455c1f0e1bae0491226e2f2d0f53bb35f7ad8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046607"
---
# <a name="cmyprovidercommand-myproviderrsh"></a>CMyProviderCommand (MyProviderRS.H)

La `CMyProviderCommand` clase es la implementación para el objeto de comando del proveedor. Proporciona la implementación para el `IAccessor`, `ICommandText`, y `ICommandProperties` interfaces. El `IAccessor` interfaz es el mismo que del conjunto de filas. El objeto de comando utiliza el descriptor de acceso para especificar enlaces de parámetros. El objeto de conjunto de filas utiliza para especificar enlaces para las columnas de salida. El `ICommandText` interfaz es una forma útil para especificar un comando textualmente. Este ejemplo se usa el `ICommandText` interfaz más adelante, cuando agrega código personalizado; también invalida la `ICommand::Execute` método. El `ICommandProperties` interfaz controla todas las propiedades de los objetos de comando y conjunto de filas.  
  
```cpp  
// CMyProviderCommand  
class ATL_NO_VTABLE CMyProviderCommand :   
class ATL_NO_VTABLE CMyProviderCommand :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IAccessorImpl<CMyProviderCommand>,  
   public ICommandTextImpl<CMyProviderCommand>,  
   public ICommandPropertiesImpl<CMyProviderCommand>,  
   public IObjectWithSiteImpl<CMyProviderCommand>,  
   public IConvertTypeImpl<CMyProviderCommand>,  
   public IColumnsInfoImpl<CMyProviderCommand>  
```  
  
El `IAccessor` interfaz administra todos los enlaces utilizados en comandos y conjuntos de filas. El consumidor llama a `IAccessor::CreateAccessor` con una matriz de `DBBINDING` estructuras. Cada `DBBINDING` estructura contiene información sobre cómo deben controlarse los enlaces de columna (por ejemplo, tipo y longitud). El proveedor recibe las estructuras y, a continuación, determina cómo se deben transferir los datos y si es necesaria ninguna conversión. El `IAccessor` interfaz se utiliza en el objeto de comando para controlar los parámetros en el comando.  
  
El objeto de comando también proporciona una implementación de `IColumnsInfo`. OLE DB requiere el `IColumnsInfo` interfaz. La interfaz permite al consumidor recuperar información acerca de los parámetros del comando. El objeto de conjunto de filas utiliza el `IColumnsInfo` interfaz para devolver información acerca de las columnas de salida para el proveedor.  
  
El proveedor también contiene una interfaz denominada `IObjectWithSite`. El `IObjectWithSite` interfaz se implementó en ATL 2.0 y permite al implementador pasar información sobre sí mismo a su elemento secundario. El objeto de comando utiliza el `IObjectWithSite` información para indicar a cualquiera genera objetos de conjunto de filas que los creó.  
  
## <a name="see-also"></a>Vea también  

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)