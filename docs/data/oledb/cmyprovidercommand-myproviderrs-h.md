---
title: "CMyProviderCommand (MyProviderRS.H) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cmyprovidercommand"
  - ""myproviderrs.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMyProviderCommand (clase): MyProviderRS.H"
  - "proveedores OLE DB, archivos generados por el asistente"
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderCommand (MyProviderRS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMyProviderCommand` es la implementación para el objeto de comando del proveedor.  Proporciona la implementación para las interfaces `IAccessor`, `ICommandText` e **ICommandProperties**.  La interfaz `IAccessor` es la misma que la del conjunto de filas.  El objeto de comando utiliza el descriptor de acceso para especificar enlaces de parámetros.  El objeto de conjunto de filas los utiliza para especificar enlaces de columnas de resultados.  La interfaz `ICommandText` proporciona una forma útil de especificar un comando de forma textual.  En este ejemplo se utiliza posteriormente la interfaz `ICommandText` al agregar código personalizado; también se reemplaza el método `ICommand::Execute`.  La interfaz **ICommandProperties** controla todas las propiedades de los objetos de comando y de conjunto de filas.  
  
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
  
 La interfaz `IAccessor` administra todos los enlaces utilizados en comandos y conjuntos de filas.  El consumidor llama a **IAccessor::CreateAccessor** con una matriz de estructuras **DBBINDING**.  Cada estructura **DBBINDING** contiene la información sobre cómo controlar los enlaces de columna \(como tipo y longitud\).  El proveedor recibe las estructuras y determina cómo deben transferirse los datos y si es necesario realizar conversiones.  La interfaz `IAccessor` se utiliza en el objeto de comando para controlar los parámetros del comando.  
  
 El objeto de comando también proporciona una implementación de `IColumnsInfo`.  OLE DB requiere la interfaz `IColumnsInfo`.  La interfaz permite al consumidor recuperar información acerca de los parámetros del comando.  El objeto de conjunto de filas utiliza la interfaz `IColumnsInfo` para devolver al proveedor información acerca de las columnas de resultados.  
  
 El proveedor también contiene una interfaz denominada `IObjectWithSite`.  La interfaz `IObjectWithSite` se implementó en ATL 2.0 y permite al implementador pasar información acerca de sí mismo al objeto secundario.  El objeto de comando utiliza la información de `IObjectWithSite` para indicar a los objetos de conjunto de filas generados el programador que los creó.  
  
## Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)