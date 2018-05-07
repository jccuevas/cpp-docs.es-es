---
title: CMyProviderCommand (MyProviderRS.H) | Documentos de Microsoft
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
ms.openlocfilehash: 8c18742d9b3b1039033ad8d42939e0f5a4578fbb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmyprovidercommand-myproviderrsh"></a>CMyProviderCommand (MyProviderRS.H)
La `CMyProviderCommand` clase es la implementación para el objeto de comando de proveedor. Proporciona la implementación para la `IAccessor`, `ICommandText`, y **ICommandProperties** interfaces. La `IAccessor` interfaz es la misma que del conjunto de filas. El objeto de comando utiliza el descriptor de acceso para especificar enlaces de parámetros. El objeto de conjunto de filas los utiliza para especificar enlaces para las columnas de salida. La `ICommandText` interfaz es una forma útil de especificar un comando textualmente. Este ejemplo se utiliza la `ICommandText` interfaz más adelante cuando agrega código personalizado; también invalida la `ICommand::Execute` método. El **ICommandProperties** interfaz controla todas las propiedades de los objetos de comando y el conjunto de filas.  
  
```  
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
  
 El `IAccessor` interfaz administra todos los enlaces utilizados en comandos y conjuntos de filas. El consumidor llama **IAccessor:: CreateAccessor** con una matriz de **DBBINDING** estructuras. Cada **DBBINDING** estructura contiene la información acerca de cómo se deben tratar los enlaces de columna (por ejemplo, tipo y longitud). El proveedor recibe las estructuras y, a continuación, determina cómo se deben transferir los datos y si es necesaria ninguna conversión. El `IAccessor` interfaz se utiliza en el objeto de comando para controlar los parámetros en el comando.  
  
 El objeto de comando también proporciona una implementación de `IColumnsInfo`. OLE DB requiere la `IColumnsInfo` interfaz. La interfaz permite al consumidor recuperar información acerca de los parámetros del comando. El objeto de conjunto de filas utiliza la `IColumnsInfo` interfaz para devolver información acerca de las columnas de salida para el proveedor.  
  
 El proveedor también contiene una interfaz denominada `IObjectWithSite`. El `IObjectWithSite` interfaz se implementó en ATL 2.0 y permite al implementador pasar información acerca de sí mismo a su elemento secundario. El objeto de comando utiliza el `IObjectWithSite` genera la información para indicar a cualquiera de los objetos de conjunto de filas que los creó.  
  
## <a name="see-also"></a>Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)