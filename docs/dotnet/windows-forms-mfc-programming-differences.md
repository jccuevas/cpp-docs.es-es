---
title: 'Windows Forms: diferencias de programación de MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: 136549bb457cc17293d4c7201c9836d9094eea94
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "79544824"
---
# <a name="windows-formsmfc-programming-differences"></a>Diferencias de programación entre Windows Forms y MFC

Los temas relacionados [con el uso de un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) describen la compatibilidad de mfc con Windows Forms. Si no está familiarizado con la programación con .NET Framework o con MFC, este tema proporciona información adicional sobre las diferencias de programación entre ambos.

Los formularios Windows Forms sirven para crear aplicaciones de Microsoft Windows en .NET Framework. Este marco de trabajo proporciona un conjunto de clases moderno, orientado a objetos y ampliable, que permite desarrollar complejas aplicaciones para Windows. Con formularios Windows Forms puede crear una aplicación cliente enriquecida que puede obtener acceso a una amplia gama de orígenes de datos y proporcionar utilidades de vista y edición de datos utilizando los controles de los formularios Windows Forms.

Sin embargo, si suele usar MFC, puede que esté acostumbrado a crear determinados tipos de aplicaciones que ya no son explícitamente compatibles con formularios Windows Forms. Las aplicaciones de Windows Forms son equivalentes a las aplicaciones de cuadros de diálogo MFC. Sin embargo, no proporcionan la infraestructura que les permita ser directamente compatibles con otros tipos de aplicaciones MFC como el servidor/contenedor de documentos OLE, los documentos ActiveX, la compatibilidad documento/vista para la interfaz de un único documento (SDI), la interfaz de múltiples documentos (MDI) y la interfaz de nivel superior de múltiples documentos (MTI). Puede escribir la lógica que desee para crear estas aplicaciones.

Para obtener más información acerca de las aplicaciones Windows Forms, consulte [Introducción a Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

Para obtener una aplicación de ejemplo que muestra Windows Forms se usa con MFC, vea [integración de MFC y Windows Forms](https://www.microsoft.com/download/details.aspx?id=2113).

Las siguientes características de vista o documentos MFC o de enrutamiento de comandos no tienen equivalente en formularios Windows Forms.

- Integración de Shell

   MFC controla los comandos de intercambio dinámico de datos (DDE) y los argumentos de línea de comandos que utiliza el shell cuando hace clic con el botón secundario del mouse en un documento y selecciona verbos como Abrir, Editar o Imprimir. Formularios Windows Forms no tiene integración de shell y no responde a sus verbos.

- Plantillas de documento

   En MFC, las plantillas de documento asocian una vista contenida en una ventana de marco (en modo MDI, SDI o MTI) con el documento que ha abierto. Formularios Windows Forms no tiene equivalente a las plantillas de documento.

- Documentos

   MFC registra tipos de archivo de documento y los procesa cuando abre un documento desde el shell. Formularios Windows Forms no tiene compatibilidad con documentos.

- Estados de documento

   MFC mantiene modificación de estados en el documento. Por lo tanto, cuando cierra la aplicación, cierra la última vista que contiene la aplicación o sale de Windows, MFC le pide que guarde el documento. Formularios Windows Forms no tiene compatibilidad equivalente.

- Comandos:

   MFC dispone del concepto de comandos. La barra de menús, la de herramientas y el menú contextual pueden invocar el mismo comando; por ejemplo, Cortar y Copiar. En formularios Windows Forms, los comandos son eventos estrechamente relacionados con un elemento de interfaz de usuario (como un elemento de menú); por lo tanto, tendrá que enlazar los eventos de comando explícitamente. En formularios Windows Forms, también puede controlar múltiples eventos con un único controlador. Para obtener más información, vea [conectar varios eventos a un solo controlador de eventos en Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).

- Enrutamiento de comandos

   El enrutamiento de comandos MFC permite procesar comandos a la vista o documentos activos. Dado que el mismo comando tiene a menudo diferentes significados según la vista en que se utilice (por ejemplo, Copiar se comporta de manera distinta en la vista de edición de texto que en un editor de gráficos), los comandos necesitan que los controle la vista activa. Dado que Windows Forms menús y las barras de herramientas no tienen un conocimiento inherente de la vista activa, no puede tener un controlador diferente para cada tipo de vista de los eventos **MenuItem. click** sin escribir código interno adicional.

- Mecanismo de actualización de comandos

   MFC dispone de un mecanismo de actualización de comandos. Por lo tanto, la vista o documento activos son responsables del estado de los elementos de la interfaz de usuario (por ejemplo, la habilitación o deshabilitación de un elemento de menú o de un botón de la barra de herramientas y estados de activación). Formularios Windows Forms no tiene un equivalente del mecanismo de actualización de comandos.

## <a name="see-also"></a>Consulte también

[Usar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
