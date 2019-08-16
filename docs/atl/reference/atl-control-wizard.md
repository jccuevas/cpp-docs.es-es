---
title: Asistente para controles ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: 58c3ebe4c2a15aa3f0d59191c37a7f2422a63ab5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261213"
---
# <a name="atl-control-wizard"></a>Asistente para controles ATL

Inserciones en un proyecto ATL (o un proyecto MFC con compatibilidad con ATL) un control ATL. Puede usar a este asistente para insertar uno de los tres tipos de controles:

- Control estándar

- Control compuesto

- Control DHTML

Además, puede especificar un control mínimo, quitando las interfaces de la [Interfaces](../../atl/reference/interfaces-atl-control-wizard.md) lista, que se proporcionan como valores predeterminados para los controles en la mayoría de los contenedores. Puede establecer las interfaces que van a admitir para el control en el **Interfaces** página del asistente.

## <a name="remarks"></a>Comentarios

El script de registro generado por este asistente registrará sus componentes COM en HKEY_CURRENT_USER en lugar de HKEY_LOCAL_MACHINE. Para modificar este comportamiento, establezca el **registrar componentes para todos los usuarios** opción del Asistente para ATL.

## <a name="names"></a>Nombres

Especifique los nombres para el objeto, interfaz y clases que se agregarán al proyecto. Excepto para **nombre corto**, todos los demás cuadros pueden cambiarse de forma independiente. Si cambia el texto para **nombre corto**, el cambio se refleja en los nombres de todos los demás cuadros de esta página. Si cambia el **coclase** nombre en la sección de COM, el cambio se refleja en el **tipo** cuadro, pero la **interfaz** nombre y **ProgID** hacer No cambie. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables por usted a medida que desarrolla el control.

> [!NOTE]
>  **Coclase** es editable en sólo los controles sin atributos. Si su proyecto tiene atributos, no puede editar **coclase**.

### <a name="c"></a>C++

Proporciona información para la clase de C++ creada para implementar el objeto.

- **Nombre corto**

   Establece el nombre abreviado para el objeto. El nombre que proporcione determina la clase y **coclase** nombres, el archivo (. CPP y. H) nombres de, el nombre de la interfaz y el **tipo** nombres, a menos que cambie esos campos individualmente.

- **Clase**

   Establece el nombre de la clase que implementa el objeto. Este nombre se basa en el nombre que se proporciona en **nombre corto**, precedidos por 'C', el prefijo habitual para un nombre de clase.

- **Archivo .h**

   Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar**.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Archivo .cpp**

   Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Con atributos**

   Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está activada y no está disponible para cambiar. Es decir, puede agregar solo los objetos con atributos a un proyecto creado con el soporte técnico de atributo.

   Puede agregar un objeto con atributos sólo a un proyecto ATL que utiliza atributos. Si selecciona esta opción para un proyecto ATL que no es compatible con atributos, el asistente le pedirá que especifique si desea agregar compatibilidad para el proyecto.

   De forma predeterminada, cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación está seleccionada). Puede desactivar esta casilla para agregar un objeto que no utiliza atributos.

   Consulte [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.

### <a name="com"></a>COM

Proporciona información sobre la funcionalidad de COM para el objeto.

- **Coclase**

   Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.

   > [!NOTE]
   > Si crea el proyecto mediante atributos, o si se indican en esta página del asistente que utiliza atributos en el control, no se puede cambiar esta opción ya que ATL no incluye el **coclase** atributo.

- **Interface**

   Establece el nombre de la interfaz para el objeto. De forma predeterminada un nombre de interfaz llevan el prefijo "I".

- **Type**

   Establece la descripción del objeto que va a aparecer en el registro

- **ProgID**

   Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto. Este campo no se rellena automáticamente. Si no rellena este campo manualmente, el control no esté disponible para otras herramientas. Por ejemplo, los controles ActiveX que se generan sin un `ProgID` no están disponibles en el **insertar ActiveX Control** cuadro de diálogo. Para más información sobre el cuadro de diálogo, vea [Insertar control ActiveX (cuadro de diálogo)](../../windows/insert-activex-control-dialog-box.md).

## <a name="see-also"></a>Vea también

[Control ATL](../../atl/reference/adding-an-atl-control.md)<br/>
[Agregar funciones al control compuesto](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)
