---
title: "Asistente para proveedores OLE DB ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.provider.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para proveedores OLE DB ATL"
  - "ATL projects, agregar proveedores OLE DB ATL"
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Asistente para proveedores OLE DB ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este asistente crea las clases que componen un proveedor OLE DB.  
  
## Comentarios  
 A partir de [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)], el script de registro generado por este asistente registrará sus componentes COM bajo **HKEY\_CURRENT\_USER** en lugar de bajo **HKEY\_LOCAL\_MACHINE**.  Para modificar este comportamiento, defina la opción **Registrar componente para todos los usuarios** del Asistente para ATL.  
  
 La tabla siguiente describe las opciones del Asistente para proveedores OLE DB ATL:  
  
 **Nombre corto**  
 Escriba el nombre corto del proveedor que se va a crear.  El resto de cuadros de edición del asistente se rellenarán automáticamente en función del contenido de este cuadro.  Puede modificar los otros cuadros de nombre si lo desea.  
  
 **Coclase**  
 Nombre de la coclase.  El nombre de ProgID cambiará para coincidir con este nombre  
  
 **Con atributos**  
 Esta opción especifica si el asistente creará clases de proveedor mediante atributos o declaraciones de plantilla.  Al seleccionar esta opción, el asistente usa atributos en lugar de declaraciones de plantilla \(la opción predeterminada si se creó un proyecto con atributos\).  Al desactivar esta opción, el asistente usa declaraciones de plantilla en lugar de atributos \(la opción predeterminada si se creó un proyecto sin atributos\).  
  
 Si selecciona esta opción habiendo creado un proyecto sin atributos, el asistente le advertirá de que el proyecto se convertirá a un proyecto con atributos y le pedirá que confirme si desea continuar.  
  
 **Id. de programa**  
 El identificador de programa es una cadena de texto que las aplicaciones pueden usar en lugar de un identificador GUID.  El nombre de ProgID tiene la forma *NombreProyecto*.*NombreCoclase.*  
  
 **Versión**  
 Número de versión del proveedor.  El valor predeterminado es 1  
  
 **Clase DataSource**  
 Nombre de la clase de origen de datos, con la forma C `Shortname` Source.  
  
 **Archivo .h de DataSource**  
 Archivo de encabezado de la clase de origen de datos.  Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente  
  
 **Clase Session**  
 Nombre de la clase de sesión, con la forma C `Shortname` Session.  
  
 **Archivo .h de Session**  
 Archivo de encabezado para la clase de sesión.  Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente  
  
 **Clase Command**  
 Nombre de la clase de comando, con la forma C `Shortname` Command.  
  
 **Archivo .h de Command**  
 Archivo de encabezado para la clase de comando.  Este nombre no se puede editar y depende del nombre del archivo de encabezado del conjunto de filas  
  
 **Clase Rowset**  
 Nombre de la clase de conjunto de filas, con la forma C `Shortname` Rowset.  
  
 **Archivo .h de Rowset**  
 Nombre de archivo de encabezado para la clase rowset.  Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente  
  
 **Archivo .cpp de Rowset**  
 Archivo de implementación del proveedor.  Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente  
  
## Vea también  
 [ATL OLE DB Provider](../../atl/reference/adding-an-atl-ole-db-provider.md)