---
title: Asistente para componentes de páginas Active Server ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.overview
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: f020ed9b58f631bfff09fe54c70e36146eb03368
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288095"
---
# <a name="atl-active-server-page-component-wizard"></a>Asistente para componentes de páginas Active Server ATL

Este asistente, inserta en el proyecto de un componente de páginas Active Server (ASP). Microsoft Internet Information Services (IIS) utiliza los componentes ASP como parte de su arquitectura de desarrollo de páginas Web.

Con este asistente, puede especificar que el componente de subprocesamiento del modelo y su compatibilidad con la agregación. También puede indicar la compatibilidad con la interfaz de la información de errores, puntos de conexión y el cálculo de referencias de subprocesamiento libre.

> [!WARNING]
> En Visual Studio 2017 versión 15.9, este asistente de código ha quedado en desuso y se quitará en una versión futura de Visual Studio. Este asistente se usa con muy poca frecuencia. La compatibilidad general con ATL y MFC no se ve afectada por la eliminación de este asistente. Si quiere compartir sus comentarios sobre este desuso, rellene [esta encuesta](https://www.surveymonkey.com/r/QDWKKCN). Su opinión es importante para nosotros.

## <a name="remarks"></a>Comentarios

A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca el **registrar componentes para todos los usuarios** opción del Asistente para ATL.

## <a name="names"></a>Nombres

Especifique los nombres para el objeto, interfaz y clases que se agregarán al proyecto. Excepto para **nombre corto**, todos los demás cuadros se pueden editar independientemente de los demás. Si cambia el texto para **nombre corto**, el cambio se refleja en los nombres de todos los demás cuadros de esta página.

Si cambia el **coclase** nombre en la sección de COM, el cambio se refleja en el **tipo** y **ProgID** cuadros, pero la **interfaz** nombre no cambia. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables por usted a medida que desarrolla el control.

### <a name="c"></a>C++

Proporciona información sobre la clase de C++ creada para el objeto.

- **Nombre corto**

   Establece el nombre de raíz para el objeto. El nombre que proporcione determina la `Class` y **coclase** nombres, el **archivo .cpp** y **archivo .h** nombres, el **interfaz**nombre, el **tipo** nombres y el **ProgID**, a menos que cambie estos campos individualmente.

- **Archivo .h**

   Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Clase**

   Establece el nombre de la clase que se va a crear. Este nombre se basa en el nombre que se proporciona en **nombre corto**, precedidos por 'C', el prefijo habitual para un nombre de clase.

- **Archivo .cpp**

   Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Con atributos**

   Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está activada y no está disponible para cambiar. Es decir, puede agregar solo los objetos con atributos a un proyecto creado con el soporte técnico de atributo.

   Si selecciona esta opción para un proyecto ATL que no es compatible con atributos, el asistente le pedirá que especifique si desea agregar compatibilidad para el proyecto.

   De forma predeterminada para los proyectos sin atributos, cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación está seleccionada). Puede desactivar esta casilla para agregar un objeto que no utiliza atributos.

   Consulte [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.

### <a name="com"></a>COM

Proporciona información sobre la funcionalidad de COM para el objeto.

- **Coclase**

   Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto. Si su proyecto o este objeto utiliza atributos, no se puede cambiar esta opción ya que ATL no incluye el **coclase** atributo.

- **Type**

   Establece la descripción del objeto que va a aparecer en el registro para la coclase.

- **Interface**

   Establece la interfaz que crea para el objeto. Esta interfaz contiene los métodos personalizados.

- **ProgID**

   Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto.

## <a name="see-also"></a>Vea también

[Componente de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
