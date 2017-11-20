---
title: Asistente para proveedores ATL OLE DB | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.provider.overview
dev_langs: C++
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 170f10d06112969d9147c37b20572f0888140d0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="atl-ole-db-provider-wizard"></a>Asistente para proveedores OLE DB ATL
Este asistente crea las clases que componen un proveedor OLE DB.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM bajo **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la **registrar componente para todos los usuarios** opción del Asistente para ATL.  
  
 En la tabla siguiente se describe las opciones para el Asistente para proveedores OLE DB ATL:  
  
 **Nombre corto**  
 Escriba el nombre corto del proveedor que se va a crear. Los otros cuadros de edición en el asistente se rellenan automáticamente en función de lo que escribe aquí. Puede modificar los otros cuadros de nombre si lo desea.  
  
 **(Coclase)**  
 El nombre de la coclase. El nombre de ProgID cambiará para coincidir con este nombre.  
  
 **El atributo**  
 Esta opción especifica si el asistente creará clases de proveedor mediante atributos o declaraciones de plantilla. Cuando se selecciona esta opción, el asistente usa atributos en lugar de declaraciones de plantilla (esta es la opción predeterminada si se creó un proyecto con atributos). Cuando desactiva esta opción, el asistente usa declaraciones de plantilla en lugar de atributos (esta es la opción predeterminada si se creó un proyecto sin atributos).  
  
 Si selecciona esta opción al crear un proyecto sin atributos, el asistente le advertirá de que el proyecto se convertirá en un proyecto con atributos y le pregunta si desea continuar o no.  
  
 **Id. de programa**  
 El ProgID o el identificador de programación, es una cadena de texto que puede usar la aplicación en lugar de un GUID. El nombre de ProgID tiene la forma *Projectname.Coclassname*.  
  
 **Versión**  
 El número de versión del proveedor. El valor predeterminado es 1.  
  
 **Clase de origen de datos**  
 El nombre de la clase de origen de datos del formulario C*Shortname*origen.  
  
 **Archivo .h de DataSource**  
 El archivo de encabezado para la clase de origen de datos. Puede editar el nombre de este archivo o seleccione un archivo de encabezado existente.  
  
 **Clase de sesión**  
 El nombre de la clase de sesión, el formato C*Shortname*sesión.  
  
 **Archivo .h de Session**  
 El archivo de encabezado para la clase de sesión. Puede editar el nombre de este archivo o seleccione un archivo de encabezado existente.  
  
 **Clase de comando**  
 El nombre de la clase de comando, el formato C*Shortname*comando.  
  
 **Archivo .h de Command**  
 El archivo de encabezado para la clase de comando. Este nombre no se puede editar y depende del nombre del archivo de encabezado de conjunto de filas.  
  
 **Clase de conjunto de filas**  
 El nombre de la clase de conjunto de filas, del formulario C*Shortname*conjunto de filas.  
  
 **Archivo .h de Rowset**  
 El archivo de encabezado para la clase de conjunto de filas. Puede editar el nombre de este archivo o seleccione un archivo de encabezado existente.  
  
 **Archivo .cpp de Rowset**  
 Archivo de implementación del proveedor. Puede editar el nombre de este archivo o seleccione un archivo de implementación existente.  
  
## <a name="see-also"></a>Vea también  
 [Proveedor OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-provider.md)

