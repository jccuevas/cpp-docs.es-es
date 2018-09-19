---
title: Implementar páginas de propiedades | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f69dab9dfc9216d1c56ed54730d5f94cbb58b1db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088740"
---
# <a name="implementing-property-pages"></a>Implementar páginas de propiedades

Páginas de propiedades son objetos COM que implementan la `IPropertyPage` o `IPropertyPage2` interfaz. ATL proporciona compatibilidad para implementar páginas de propiedades a través de la [Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md) en el [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md).

Para crear una página de propiedades mediante ATL:

- Cree o abra un proyecto de servidor de biblioteca (DLL) de vínculos dinámicos ATL.

- Abra el [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md) y seleccione **página de propiedades ATL**.

- Asegúrese de que la página de propiedades es un apartamento de subproceso (porque tiene una interfaz de usuario).

- Establezca el título, la descripción (cadena) y el archivo de ayuda que se asociará con la página.

- Agregar controles al recurso de cuadro de diálogo generado para que actúe como la interfaz de usuario de la página de propiedades.

- Responder a cambios en la interfaz de usuario de la página para realizar la validación, actualizar el sitio de la página o actualizar los objetos asociados a la página. En concreto, llame a [IPropertyPageImpl:: SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) cuando el usuario realiza cambios en la página de propiedades.

- Opcionalmente, invalidar el `IPropertyPageImpl` métodos mediante las instrucciones siguientes.

   |IPropertyPageImpl (método)|Si desea reemplazar...|Notas|  
   |------------------------------|----------------------------------|-----------|  
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Realizar comprobaciones de integridad básica en el número de objetos que se pasan a la página y las interfaces que admiten.|Ejecutar su propio código antes de llamar a la implementación de la clase base. Si los objetos que se va a establecer no satisface sus expectativas, debe anular la llamada tan pronto como sea posible.|  
   |[Activar](../atl/reference/ipropertypageimpl-class.md#activate)|Inicializar la interfaz de usuario de la página (por ejemplo, establecer controles de cuadro de diálogo con los valores de propiedad actuales de los objetos, crear dinámicamente controles o realizar otras inicializaciones).|Llame a la implementación de clase base antes que el código para que la clase base tiene una oportunidad para crear la ventana de cuadro de diálogo y todos los controles antes de actualizarlos.|  
   |[aplicar](../atl/reference/ipropertypageimpl-class.md#apply)|Validar los valores de propiedad y actualizar los objetos.|No hay ninguna necesidad de llamar a la implementación de clase base, ya que no hace nada aparte de seguimiento de la llamada.|  
   |[Desactivar](../atl/reference/ipropertypageimpl-class.md#deactivate)|Limpiar los elementos relacionados con la ventana.|La implementación de la clase base destruye el cuadro de diálogo que representa la página de propiedades. Si necesita limpiar antes de destruir el cuadro de diálogo, debe agregar el código antes de llamar a la clase base.|

Para una implementación de página de propiedades de ejemplo, vea [ejemplo: implementar una página de propiedades](../atl/example-implementing-a-property-page.md).

> [!NOTE]
> Si desea hospedar controles ActiveX en su página de propiedades, deberá cambiar la derivación de la clase generada por el asistente. Reemplace **CDialogImpl\<CSuClase >** con **CAxDialogImpl\<CSuClase >** en la lista de clases base.

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../atl/atl-com-property-pages.md)<br/>
[Ejemplo ATLPages](../visual-cpp-samples.md)
