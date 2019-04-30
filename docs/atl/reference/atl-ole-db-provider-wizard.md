---
title: Asistente para proveedores OLE DB ATL
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.atl.provider.overview
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: 3f8ff69fd80056bc2ac5a52cf3f42c69f8e8c543
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248268"
---
# <a name="atl-ole-db-provider-wizard"></a>Asistente para proveedores OLE DB ATL

Este asistente crea las clases que componen un proveedor OLE DB.

> [!WARNING]
> En Visual Studio 2017 versión 15.9, este asistente de código ha quedado en desuso y se quitará en una versión futura de Visual Studio. Este asistente se usa con muy poca frecuencia. La compatibilidad general con ATL y MFC no se ve afectada por la eliminación de este asistente. Si quiere compartir sus comentarios sobre este desuso, rellene [esta encuesta](https://www.surveymonkey.com/r/QDWKKCN). Su opinión es importante para nosotros.

## <a name="remarks"></a>Comentarios

A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca el **registrar componentes para todos los usuarios** opción del Asistente para ATL.

En la tabla siguiente se describe las opciones para el Asistente para proveedores OLE DB ATL:

- **Nombre corto**

   Escriba el nombre corto del proveedor que se va a crear. Los otros cuadros de edición en el asistente se rellenarán automáticamente en función de lo que escribe aquí. Puede modificar los otros cuadros de nombre si lo desea.

- **Coclase**

   El nombre de la coclase. El nombre de ProgID cambiará para coincidir con este nombre.

- **Con atributos**

   Esta opción especifica si el asistente creará clases de proveedor mediante atributos o declaraciones de plantilla. Cuando se selecciona esta opción, el asistente utiliza atributos en lugar de declaraciones de plantilla (es la opción predeterminada si ha creado un proyecto con atributos). Cuando desactiva esta opción, el asistente utiliza las declaraciones de plantilla en lugar de atributos (la opción predeterminada si ha creado un proyecto sin atributos).

   Si selecciona esta opción al crear un proyecto sin atributos, el asistente le advertirá de que el proyecto se convertirá en un proyecto con atributos y le preguntará si desea continuar o no.

- **ProgID**

   El ProgID o el identificador de programación, es una cadena de texto que puede usar la aplicación en lugar de un GUID. El nombre de ProgID tiene la forma *Projectname.Coclassname*.

- **Versión**

   El número de versión del proveedor. El valor predeterminado es 1.

- **Clase de origen de datos**

   El nombre de la clase de origen de datos del formulario C*Shortname*origen.

- **Archivo .h de origen de datos**

   El archivo de encabezado para la clase de origen de datos. Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente.

- **Clase de sesión**

   El nombre de la clase de sesión del formulario C*Shortname*sesión.

- **Archivo .h de sesión**

   El archivo de encabezado para la clase de sesión. Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente.

- **Clase de comando**

   El nombre de la clase de comando del formulario C*Shortname*comando.

- **Archivo .h de Command**

   El archivo de encabezado para la clase de comando. Este nombre no se puede editar y depende del nombre del archivo de encabezado del conjunto de filas.

- **Clase de conjunto de filas**

   El nombre de la clase de conjunto de filas, del formulario C*Shortname*conjunto de filas.

- **Archivo .h de Rowset**

   El archivo de encabezado para la clase de conjunto de filas. Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente.

- **Archivo .cpp de Rowset**

   Archivo de implementación del proveedor. Puede editar este nombre de archivo o seleccionar un archivo de implementación existente.

## <a name="see-also"></a>Vea también

[Proveedor OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-provider.md)
