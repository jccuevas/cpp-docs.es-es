---
title: Asistente para componentes ATL COM+ 1.0
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.atl.mts.overview
helpviewer_keywords:
- ATL projects, adding components
- ATL COM+ 1.0 Component Wizard
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: 227dda9518b67b410f52db8c6efb33bbc2c8f1b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513781"
---
# <a name="atl-com-10-component-wizard"></a>Asistente para componentes ATL COM+ 1.0

Use este asistente para agregar un objeto al proyecto que admita servicios COM + 1.0, incluidas las transacciones.

Puede especificar si el objeto admite interfaces duales y automatización. También puede indicar la compatibilidad con la interfaz de la información de error, control de objeto mejorada, transacciones y asincrónica message Queue Server.

> [!WARNING]
> En Visual Studio 2017 versión 15.9, este asistente de código ha quedado en desuso y se quitará en una versión futura de Visual Studio. Este asistente se usa con muy poca frecuencia. La compatibilidad general con ATL y MFC no se ve afectada por la eliminación de este asistente. Si quiere compartir sus comentarios sobre este desuso, rellene [esta encuesta](https://www.surveymonkey.com/r/QDWKKCN). Su opinión es importante para nosotros.

## <a name="remarks"></a>Comentarios

A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca el **registrar componentes para todos los usuarios** opción del Asistente para ATL.

## <a name="names"></a>Nombres

Especifique los nombres para el objeto, interfaz y clases que se agregarán al proyecto. Con la excepción de **nombre corto**, todos los demás cuadros se pueden editar independientemente de los demás. Si cambia el texto para **nombre corto**, el cambio se refleja en los nombres de todos los demás cuadros de esta página. Si cambia el **coclase** nombre en la sección de COM, el cambio se refleja en el **tipo** y **ProgID** cuadros, pero la **interfaz** nombre no cambia. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables por usted a medida que desarrolla el control.

- **Nombre corto**

   Establece el nombre abreviado para el objeto. El nombre que proporcione determina la `Class` y `Coclass` nombres, el **archivo .cpp** y **archivo .h** nombres, el **interfaz** nombre, el **Tipo** nombres y el **ProgID**, a menos que cambie estos campos individualmente.

- **Archivo .h**

   Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Clase**

   Establece el nombre de la clase que se va a crear. Este nombre se basa en el nombre que proporcione en **nombre corto**, precedidos por 'C', el prefijo habitual para un nombre de clase.

- **Archivo .cpp**

   Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Con atributos**

   Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está activada y no está disponible para cambiar. Es decir, puede agregar solo los objetos con atributos a un proyecto creado con el soporte técnico de atributo.

   Si selecciona esta opción para un proyecto ATL que no es compatible con atributos, el asistente le pedirá que especifique si desea agregar compatibilidad para el proyecto.

   Cualquier objeto que agregue después de establecer esta opción se designará como atributos de forma predeterminada (la casilla de verificación está seleccionada). Puede desactivar esta casilla para agregar un objeto que no utiliza atributos.

   Consulte [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.

### <a name="com"></a>COM

Proporciona información sobre la funcionalidad de COM para el objeto.

- **Coclase**

   Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.

> [!NOTE]
>  Si crea el proyecto mediante atributos, o si se indican en esta página del asistente que el componente COM + 1.0 utiliza atributos, no se puede cambiar esta opción ya que ATL no incluye el `coclass` atributo.

- **Type**

   Establece la descripción del objeto que va a aparecer en el registro

- **Interface**

   Establece la interfaz que crea para el objeto. Esta interfaz contiene los métodos personalizados.

- **Id. de programa**

   Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto.

## <a name="see-also"></a>Vea también

[Componente COM + 1.0 ATL](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

