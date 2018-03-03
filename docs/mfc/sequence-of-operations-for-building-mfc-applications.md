---
title: Secuencia de operaciones para compilar aplicaciones MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], developing
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae1169b438a181e22696502352c19353421469b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-building-mfc-applications"></a>Secuencia de operaciones para compilar aplicaciones MFC
En la tabla siguiente se explica la secuencia general que normalmente puede seguir a medida que desarrolla la aplicación MFC.  
  
### <a name="sequence-for-building-an-application-with-the-framework"></a>Secuencia para la creación de una aplicación con el marco de trabajo  
  
|Tarea|Lo hace|El marco de trabajo|  
|----------|------------|------------------------|  
|Crear una aplicación esqueleto.|Ejecute el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md). Especifique las opciones que desee en las páginas de opciones. Las opciones incluyen hacer que la aplicación a un componente COM, contenedor o ambos; agregar automatización; y hacer que la aplicación sea compatible con la base de datos.|El Asistente para aplicaciones MFC crea los archivos para una aplicación esqueleto, incluidos los archivos de origen para la aplicación, documento, vista y ventanas de marco; un archivo de recursos; un archivo de proyecto; y otros usuarios, todos ellos personalizados según según sus especificaciones.|  
|Vea lo que el marco de trabajo y el Asistente para aplicaciones MFC ofrecen sin agregar una línea de su propio código.|Compile la aplicación esqueleto y ejecútelo en Visual C++.|La aplicación esquema en ejecución deriva muchos estándar **archivo**, **editar**, **vista**, y **ayuda** comandos de menú desde el marco de trabajo. Para las aplicaciones MDI, también obtendrá un menú de Windows totalmente funcional y el marco de trabajo administra la creación, la organización y la destrucción de ventanas secundarias MDI.|  
|Construir la interfaz de usuario de la aplicación.|Usar Visual C++ [editores de recursos](../windows/resource-editors.md) para editar visualmente la interfaz de usuario de la aplicación:<br /><br /> -Crear menús.<br />-Definir aceleradores.<br />-Crear cuadros de diálogo.<br />-Crear y editar mapas de bits, iconos y cursores.<br />-Modificar la barra de herramientas que se crea automáticamente el Asistente para aplicaciones MFC.<br />-Crear y editar otros recursos.<br /><br /> También puede probar los cuadros de diálogo en el editor de cuadro de diálogo.|El archivo de recursos predeterminado creado por el Asistente para aplicaciones MFC proporciona muchos de los recursos que necesita. Visual C++ permite editar los recursos existentes y agregar nuevos recursos fácilmente y visualmente.|  
|Los menús se asignan a funciones del controlador.|Use la **eventos** botón en el [ventana propiedades](/visualstudio/ide/reference/properties-window) para conectar menús y aceleradores para controlar funciones en el código.|La ventana Propiedades inserta entradas del mapa de mensajes y plantillas de función vacías en los archivos de origen que especifique y administra muchas tareas de codificación manuales.|  
|Escribir el código del controlador.|Use la vista de clases para saltar directamente al código en el editor de código fuente. Rellene el código de las funciones de controlador. Para obtener más información sobre el uso de la vista de clases y los asistentes que agregan código a un proyecto, vea [agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md).|Vista de clases abre el editor, se desplaza a la plantilla de función vacía y coloca el cursor para usted.|  
|Botones de barra de herramientas se asignan a los comandos.|Cada botón en la barra de herramientas se asignan a un comando de menú o tecla aceleradora asignando el botón, el identificador de comando adecuado.|El marco de trabajo controla el dibujo, habilitar, deshabilitar, comprobación y otros aspectos visuales de los botones de barra de herramientas.|  
|Probar las funciones de controlador.|Volver a generar el programa y utilizar las herramientas de depuración integradas para comprobar que los controladores funcionan correctamente.|Puede paso a paso o a través del código para ver cómo se llama a los controladores de seguimiento. Si ha rellenado el código del controlador, los controladores de llevar a cabo comandos. El marco de trabajo deshabilitará automáticamente los elementos de menú y botones de barra de herramientas que no se controlan.|  
|Agregar [cuadros de diálogo](../mfc/dialog-boxes.md).|Recursos de plantilla de cuadro de diálogo se han diseñado con el editor de cuadro de diálogo. A continuación, cree una clase de cuadro de diálogo y el código que controla el cuadro de diálogo.|El marco de trabajo administra el cuadro de diálogo y facilita la recuperación de información introducida por el usuario.|  
|Inicializar, validar y recuperar datos de cuadro de diálogo.|También puede definir cómo son los controles del cuadro de diálogo se inicializa y se validen. Usar Visual Studio para agregar variables miembro a la clase de cuadro de diálogo y asignarlos a los controles de cuadro de diálogo. Especificar reglas de validación que se aplicará a cada control cuando el usuario escribe datos. Proporcione sus propias validaciones si lo desea.|El marco de trabajo administra la validación e inicialización del cuadro de diálogo. Si el usuario introduce información no válida, el marco de trabajo muestra un cuadro de mensaje y permite al usuario volver a escribir los datos.|  
|Crear clases adicionales.|Utilice la vista de clases para crear documentos adicionales, vista y las clases de ventana de marco más allá de los creados automáticamente por el Asistente para aplicaciones MFC. Puede crear clases de conjunto de registros de base de datos adicionales, clases de cuadro de diálogo y así sucesivamente. (Con la vista de clases, puede crear clases no derivadas de clases MFC.)|Vista de clases agrega estas clases a los archivos de origen y le ayuda a definir sus conexiones con cualquier comando que controlen.|  
|Agregar componentes listos para usar a la aplicación.|Use el `New Item dialog box` para agregar varios elementos.|Estos elementos son fáciles de integrar en la aplicación y guardar una gran cantidad de trabajo.|  
|Implementar la clase de documento.|Implementar la clase de documento específica de la aplicación o clases. Agregue variables miembro para almacenar las estructuras de datos. Agregar funciones miembro para proporcionar una interfaz a los datos.|El marco de trabajo ya sabe cómo interactúan con los archivos de datos del documento. Puede abrir y cerrar archivos de documento, leer y escribir los datos del documento y controlar otras interfaces de usuario. Puede centrarse en cómo se manipulan los datos del documento.|  
|Implementar Abrir, guardar, comandos y guardar como.|Escribir código para el documento `Serialize` función miembro.|El marco de trabajo muestra cuadros de diálogo para la **abiertos**, **guardar**, y **Guardar como** comandos en el **archivo** menú. Escribe y lecturas hacer copia de un documento con el formato de datos especificado en su `Serialize` función miembro.|  
|Implementar la clase de vista.|Implementar una o más clases de vista correspondiente a los documentos. Implementar funciones de miembro de la vista que asignó a la interfaz de usuario con la vista de clases. Una variedad de [CView](../mfc/reference/cview-class.md)-clases derivadas están disponibles, incluida [CListView](../mfc/reference/clistview-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md).|El marco de trabajo administra la mayor parte de la relación entre un documento y su vista. Funciones de miembro de la vista tener acceso a documentos de la vista para representar su imagen en la pantalla o página impresa y actualizar las estructuras de datos del documento en respuesta a los comandos de edición de usuario.|  
|Mejorar la impresión predeterminada.|Si tiene que admitir la impresión de varias páginas, reemplazar las funciones miembro de la vista.|El marco de trabajo admite el **impresión**, **Configurar página**, y **vista previa de impresión** comandos en el **archivo** menú. Debe saber cómo dividir el documento en varias páginas.|  
|Agregar el desplazamiento.|Si tiene que admite el desplazamiento, derive la clase de vista o clases de [CScrollView](../mfc/reference/cscrollview-class.md).|La vista agrega automáticamente barras de desplazamiento cuando la ventana de vista se hace demasiado pequeña.|  
|Crear vistas de formulario.|Si desea basar las vistas en recursos de plantilla de cuadro de diálogo, derive la clase de vista o clases de [CFormView](../mfc/reference/cformview-class.md).|La vista utiliza el recurso de plantilla de cuadro de diálogo para mostrar los controles. El usuario puede cambiar mediante tabulación desde el control al control en la vista.|  
|Crear formularios de base de datos.|Si desea que una aplicación de acceso a datos basado en formularios, derive su clase de vista de [CRecordView](../mfc/reference/crecordview-class.md) (para programar con ODBC).|La vista funciona como una vista de formulario, pero sus controles están conectados a los campos de un [CRecordset](../mfc/reference/crecordset-class.md) objeto que representa una tabla de base de datos. MFC mueve datos entre los controles y el conjunto de registros.|  
|Crear editor de texto simple.|Si desea que la vista como un editor de texto simple, derive la clase de vista o clases de [CEditView](../mfc/reference/ceditview-class.md) o [CRichEditView](../mfc/reference/cricheditview-class.md).|La vista proporciona Editar funciones, compatibilidad con el Portapapeles y entrada/salida de archivos. `CRichEditView`Proporciona texto con estilo.|  
|Agregar ventanas divisoras.|Si desea admitir la división de ventanas, agregue un [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) el objeto a la ventana de marco SDI o ventana secundaria MDI y enlazar en la ventana [OnCreateClient](../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.|El marco de trabajo proporciona controles de cuadro divisor junto a las barras de desplazamiento y administra la división de la vista en varios paneles. Si el usuario divide una ventana, el marco de trabajo crea y asocia objetos de vista adicionales al documento.|  
|Compilar, probar y depurar la aplicación.|Utilice las funciones de Visual C++ para compilar, probar y depurar la aplicación.|Visual C++ permite ajustar la compilación, vínculo y otras opciones. También le permite examinar la estructura de código y la clase de origen.|  
  
## <a name="see-also"></a>Vea también  
 [Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [Compilación en el marco](../mfc/building-on-the-framework.md)

