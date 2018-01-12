---
title: "Implementar páginas de propiedades | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac80bdd9e38d14b53aea7b691d480272cce66e7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-property-pages"></a>Implementar páginas de propiedades
Páginas de propiedades son objetos COM que implementan la `IPropertyPage` o **IPropertyPage2** interfaz. ATL proporciona compatibilidad para implementar páginas de propiedades a través de la [Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md) en el [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md).  
  
 Para crear una página de propiedades con ATL:  
  
-   Cree o abra un proyecto de servidor de biblioteca (DLL) de vínculos dinámicos ATL.  
  
-   Abra la [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md) y seleccione **página de propiedades ATL**.  
  
-   Asegúrese de que la página de propiedades es un apartamento de un subproceso (porque tiene una interfaz de usuario).  
  
-   Establecer el título, la descripción (cadena) y el archivo de ayuda que se asociará con la página.  
  
-   Agregar controles al recurso de cuadro de diálogo generado para que actúe como la interfaz de usuario de la página de propiedades.  
  
-   Responder a cambios en la interfaz de usuario de la página para realizar la validación, actualizar el sitio de la página o actualizar los objetos asociados a la página. En concreto, llame a [IPropertyPageImpl:: SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) cuando el usuario realiza cambios en la página de propiedades.  
  
-   Opcionalmente, invalide el `IPropertyPageImpl` métodos siguiendo las directrices indicadas a continuación.  
  
    |Método IPropertyPageImpl|Si desea reemplazar...|Notas|  
    |------------------------------|----------------------------------|-----------|  
    |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Realizar comprobaciones básicas en el número de objetos que se pasan a la página y las interfaces que admiten.|Ejecutar su propio código antes de llamar a la implementación de la clase base. Si los objetos que se va a establecer no satisface sus expectativas, debe anular la llamada tan pronto como sea posible.|  
    |[Activar](../atl/reference/ipropertypageimpl-class.md#activate)|Inicializar la interfaz de usuario de la página (por ejemplo, establecer controles de cuadro de diálogo con los valores de propiedad actuales de los objetos, crear controles de forma dinámica o realizar otras inicializaciones).|Llame a la implementación de la clase base antes que el código para que la clase base tiene una oportunidad para crear el cuadro de diálogo y todos los controles antes de intentar actualizarlas.|  
    |[Aplicar](../atl/reference/ipropertypageimpl-class.md#apply)|Validar los valores de propiedad y actualizar los objetos.|No hay ninguna necesidad de llamar a la implementación de clase base ya que no realiza ninguna acción aparte de seguimiento de la llamada.|  
    |[Desactivar](../atl/reference/ipropertypageimpl-class.md#deactivate)|Limpiar los elementos relacionados con la ventana.|Implementación de la clase base destruye el cuadro de diálogo que representa la página de propiedades. Si necesita limpiar antes de que se destruya el cuadro de diálogo, debe agregar el código antes de llamar a la clase base.|  
  
 Para una implementación de página de propiedades de ejemplo, vea [ejemplo: implementar una página de propiedades](../atl/example-implementing-a-property-page.md).  
  
> [!NOTE]
>  Si desea hospedar controles ActiveX en la página de propiedades, debe cambiar la derivación de la clase generada por el asistente. Reemplace **CDialogImpl\<CSuClase >** con **CAxDialogImpl\<CSuClase >** en la lista de clases base.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades](../atl/atl-com-property-pages.md)   
 [Ejemplo ATLPages](../visual-cpp-samples.md)

