---
title: Implementar páginas de propiedades
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: c4ba69d8421a76a94e4a676cb62ee53936d77da3
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524581"
---
# <a name="implementing-property-pages"></a>Implementar páginas de propiedades

::: moniker range="vs-2019"

El Asistente para páginas de propiedades ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="vs-2017"

Las páginas de propiedades son objetos COM que implementan la interfaz `IPropertyPage` o `IPropertyPage2`. ATL proporciona compatibilidad con la implementación de páginas de propiedades a través del [Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md) en el [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md).

Para crear una página de propiedades mediante ATL:

- Cree o abra un proyecto de servidor de biblioteca de vínculos dinámicos (DLL) ATL.

- Abra el [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md) y seleccione **Página de propiedades ATL**.

- Asegúrese de que su página de propiedades es un subproceso de tipo apartamento (ya que tiene una interfaz de usuario).

- Establezca el título, la descripción (cadena de documento) y el archivo de ayuda que se van a asociar a su página.

- Agregue controles al recurso de cuadro de diálogo generado que actuará como interfaz de usuario de su página de propiedades.

- Responda a los cambios en la interfaz de usuario de su página para realizar la validación y actualizar el sitio de la página o los objetos asociados a esta. En concreto, llame a [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) si el usuario realiza cambios en la página de propiedades.

- De forma opcional, invalide los métodos `IPropertyPageImpl` mediante las instrucciones enumeradas a continuación.

   |Método IPropertyPageImpl|Invalide si desea...|Notas|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Realizar comprobaciones de estado básicas del número de objetos que se pasan a su página y las interfaces que admiten.|Ejecute su propio código antes de llamar a la implementación de clase base. Si los objetos que se establecen no cumplen sus expectativas, debe anular la llamada lo antes posible.|
   |[Activate](../atl/reference/ipropertypageimpl-class.md#activate)|Inicializar la interfaz de usuario de su página (por ejemplo, establezca controles de diálogo con valores de propiedades actuales desde objetos, cree controles de forma dinámica o realice otras inicializaciones).|Llame a la implementación de clase base antes que a su código para que la clase base pueda crear la ventana de diálogo y todos los controles antes de que intente actualizarlos.|
   |[Apply](../atl/reference/ipropertypageimpl-class.md#apply)|Validar la configuración de propiedades y actualizar los objetos.|No es necesario llamar a la implementación de clase base, ya que no hace nada aparte del seguimiento de la llamada.|
   |[Deactivate](../atl/reference/ipropertypageimpl-class.md#deactivate)|Limpiar los elementos relacionados con ventanas.|La implementación de clase base destruye el cuadro de diálogo que representa la página de propiedades. Si necesita limpiar antes de que se destruya el cuadro de diálogo, debe agregar su código antes de llamar a la clase base.|

Para ver una implementación de una página de propiedades de ejemplo, consulte [Ejemplo: Implementación de una página de propiedades](../atl/example-implementing-a-property-page.md).

> [!NOTE]
> Si desea hospedar controles ActiveX en su página de propiedades, tendrá que cambiar la derivación de su clase generada por el asistente. Reemplace **CDialogImpl\<CYourClass>** por **CAxDialogImpl\<CYourClass>** en la lista de clases base.

::: moniker-end

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../atl/atl-com-property-pages.md)<br/>
[Ejemplos de Visual C++](../overview/visual-cpp-samples.md)
