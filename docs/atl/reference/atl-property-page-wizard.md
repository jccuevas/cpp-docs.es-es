---
title: Asistente para páginas de propiedades ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94bca969b150718450da166501abaea9c89b75d7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760388"
---
# <a name="atl-property-page-wizard"></a>Asistente para páginas de propiedades ATL

Este asistente [agrega una página de propiedades en un proyecto ATL](../../atl/reference/adding-an-atl-property-page.md) o a un proyecto MFC con compatibilidad con ATL. Una página de propiedades ATL proporciona una interfaz de usuario para establecer las propiedades (o llamar a los métodos) de uno o más objetos COM.

## <a name="remarks"></a>Comentarios

A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca el **registrar componentes para todos los usuarios** opción del Asistente para ATL.

## <a name="names"></a>Nombres

Especifique los nombres para el objeto, interfaz y clases que se agregarán al proyecto. Excepto para **nombre corto**, todos los demás cuadros pueden modificarse de forma independiente. Si cambia el texto para **nombre corto**, el cambio se refleja en los nombres de todos los demás cuadros de esta página. Si cambia el **coclase** nombre en la sección de COM, el cambio se refleja en el **tipo** y **ProgID** cuadros. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables por usted a medida que desarrolla su página de propiedades.

> [!NOTE]
>  **Coclase** es editable en sólo los proyectos sin atributos. Si su proyecto tiene atributos, no puede editar **coclase**.

### <a name="c"></a>C++

Proporciona información para la clase de C++ creada para implementar el objeto.

|||
|-|-|
|Término|de esquema JSON|
|**Nombre corto**|Establece el nombre abreviado para el objeto. El nombre que proporcione determina la clase y **coclase** nombres, el archivo (**.cpp** y **.h**), los nombres de los **tipo** nombre y el  **Id. de programa**, a menos que cambie estos campos individualmente.|
|**Archivo .h**|Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.<br /><br /> El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.|
|**Clase**|Establece el nombre de la clase que implementa el objeto. Este nombre se basa en el nombre que se proporciona en **nombre corto**, precedidos por 'C', el prefijo habitual para un nombre de clase.|
|**Archivo .cpp**|Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.<br /><br /> El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.|
|**Con atributos**|Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, se selecciona esta opción y no está disponible para cambiar, es decir, puede agregar solo objetos con atributos a un proyecto creado con el soporte técnico de atributo.<br /><br /> Puede agregar un objeto con atributos sólo a un proyecto ATL que utiliza atributos. Si selecciona esta opción para un proyecto ATL que no es compatible con atributos, el asistente le pedirá que especifique si desea agregar compatibilidad para el proyecto.<br /><br /> De forma predeterminada, cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación está seleccionada). Puede desactivar esta casilla para agregar un objeto que no utiliza atributos.<br /><br /> Consulte [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.|

### <a name="com"></a>COM

Proporciona información sobre la funcionalidad de COM para el objeto.

**Coclase**  
Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.

> [!NOTE]
>  Si crea el proyecto mediante atributos, o si se indica que la página de propiedades utiliza atributos en esta página del asistente, no se puede cambiar esta opción ya que ATL no incluye el `coclass` atributo.

**Type**  
Establece la descripción del objeto que va a aparecer en el registro

**Id. de programa**  
Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto.

## <a name="see-also"></a>Vea también

[Opciones, Asistente para páginas de propiedades ATL](../../atl/reference/options-atl-property-page-wizard.md)   
[Cadenas, Asistente para páginas de propiedades ATL](../../atl/reference/strings-atl-property-page-wizard.md)   
[Ejemplo: Implementar una página de propiedades](../../atl/example-implementing-a-property-page.md)

