---
title: "Tutorial: Crear una aplicaci&#243;n de cinta usando MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "crear una aplicación de cinta (MFC)"
  - "aplicación de cinta, crear (MFC)"
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
caps.latest.revision: 21
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear una aplicaci&#243;n de cinta usando MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tutorial se muestra cómo usar el **Asistente para aplicaciones MFC** para crear una aplicación que presenta una cinta de forma predeterminada.  A continuación, se puede expandir la cinta de opciones; para ello, vamos a agregar una categoría de cinta **Personalizado** con un panel de cinta **Favoritos** y agregaremos al panel algunos comandos de uso frecuente.  
  
## Requisitos previos  
 En este tutorial se supone que ha configurado [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] para utilizar la **Configuración general de desarrollo**.  Si usa valores diferentes, algunos de los elementos de la interfaz de usuario a los que se hace referencia en las instrucciones siguientes pueden no mostrarse.  Para obtener más información acerca de cómo cambiar la configuración, vea [How to: Reset Your Settings](http://msdn.microsoft.com/es-es/c95c51be-e609-4769-abba-65e6beedec76).  
  
### Para crear una aplicación MFC con una cinta de opciones  
  
1.  Utilice **Asistente para aplicaciones MFC** para crear una aplicación MFC con una cinta.  Para ejecutar el asistente, en el menú **Archivo**, seleccione **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en **Plantillas instaladas**, expanda el nodo **Visual C\+\+**, seleccione **MFC** y, a continuación, seleccione **Aplicación MFC**.  Escriba un nombre para el proyecto, por ejemplo, `MFCRibbonApp`, y haga clic en **Aceptar**.  
  
3.  En la primera página del **Asistente para aplicaciones MFC**, haga clic en **Siguiente**.  
  
4.  En la página **Tipo de aplicación**, en **Estilo visual y colores**, seleccione **Office 2007 \(tema Azul\)**.  Deje los otros valores tal como están.  Haga clic en **Siguiente**.  
  
5.  En la página **Compatibilidad con documentos compuestos**, asegúrese de que **Ninguno** está seleccionado y haga clic en **siguiente**.  
  
6.  En la página **Prop. plantilla documento**, en el cuadro **Extensión de archivo**, escriba una extensión de nombre de archivo para los documentos que esta aplicación crea, por ejemplo, `mfcrbnapp`.  Haga clic en **Siguiente**.  
  
7.  En la página **Compatibilidad con bases de datos**, asegúrese de que **Ninguno** está seleccionado y haga clic en **Siguiente**.  
  
8.  En la página **Características de la interfaz de usuario**, asegúrese de que **Usar una cinta de opciones** está seleccionado.  Haga clic en **Siguiente**.  
  
9. De forma predeterminada, el **Asistente para aplicaciones MFC** agrega compatibilidad para varios paneles de acoplamiento.  Debido a que en este tutorial solo se enseña la cinta, puede quitar estas opciones de la aplicación.  En la página **Características avanzadas**, desactive todas las opciones.  Haga clic en **Siguiente**.  
  
10. En la página **Clases generadas**, haga clic en **Finalizar** para crear la aplicación MFC.  
  
11. Para comprobar que la aplicación se creó correctamente, compílela y ejecútela.  Para compilar la aplicación, en el menú **Generar**, haga clic en **Generar solución**.  Si la aplicación se compila correctamente, en el menú **Depurar**, haga clic en **Iniciar depuración** para ejecutarla.  
  
     El asistente crea automáticamente una cinta que tiene una categoría de cinta denominada **Inicio**.  Esta cinta contiene tres paneles de cinta, que se denominan **Portapapeles**, **Vista** y **Ventana**.  
  
### Para agregar una categoría y un panel a la cinta  
  
1.  Para abrir el recurso de cinta creado por el asistente, en el menú **Vista**, elija **Otras ventanas** y haga clic en **Vista de recursos**.  En **Vista de recursos**, haga clic en **Cinta** y haga doble clic en **IDR\_RIBBON**.  
  
2.  Primero, agregue una categoría personalizada a la cinta de opciones haciendo doble clic en **Categoría** en el **Cuadro de herramientas**.  
  
     Se crea una categoría que tiene el título **Category1**.  De forma predeterminada, la categoría contiene un panel.  
  
     Haga clic con el botón secundario en **Category1** y, a continuación, haga clic en **Propiedades**.  En la ventana **Propiedades**, cambie la propiedad **Caption** a `Personalizado`.  
  
     Las propiedades **Large Images** y **Small Images** especifican los mapas de bits que se utilizan como iconos de los elementos de la cinta en esta categoría.  Dado que la creación de mapas de bits personalizados está fuera del ámbito de este tutorial, simplemente reutilice los mapas de bits creados por el asistente.  Los mapas de bits pequeños son de 16 por 16 píxeles.  Para las imágenes pequeñas, utilice los mapas de bits a los que se tiene acceso mediante el identificador de recursos IDB\_FILESMALL.  Los mapas de bits grandes son de 32 por 32 píxeles.  Para las imágenes grandes, utilice los mapas de bits a los que se tiene acceso mediante el identificador de recursos IDB\_FILELARGE.  
  
    > [!NOTE]
    >  En las pantallas HDPI \(Gran número de puntos por pulgada\), se usan automáticamente las versiones HDPI de las imágenes.  
  
3.  A continuación, personalice el panel.  Los paneles se usan para agrupar los elementos que se relacionan lógicamente entre sí.  Por ejemplo, en la pestaña **Inicio** de esta aplicación, los comandos **Cortar**, **Copiar** y **Pegar** se encuentran en el panel **Portapapeles**.  Para personalizar el panel, haga clic con el botón secundario en **Panel1** y haga clic en **Propiedades**.  En la ventana **Propiedades**, cambie la propiedad **Caption** a `Favoritos`.  
  
     Puede especificar **Image Index** para el panel.  Este número especifica el icono que se muestra si el panel de la cinta se agrega a la **Barra de herramientas de acceso rápido**.  El icono no aparece en el propio panel de la cinta.  
  
4.  Para comprobar que la categoría y el panel de la cinta se crearon correctamente, obtenga una vista previa del control de cinta.  En la **Barra de herramientas del editor de Ribbon**, haga clic en el botón **Ribbon de prueba**.  Se deben mostrar una pestaña **Personalizado** y un panel **Favoritos** en la cinta.  
  
### Para agregar elementos a los paneles de la cinta  
  
1.  Para agregar elementos al panel que creó en el procedimiento anterior, arrastre controles de la sección **Editor de Ribbon** del **Cuadro de herramientas** al panel en la vista Diseño.  
  
2.  Primero, agregue un botón **Imprimir**.  El botón **Imprimir** tendrá un submenú que contiene un comando **Impresión rápida**, que usa la impresora predeterminada para imprimir.  Ambos comandos ya se han definido para esta aplicación.  Se encuentran en el menú de la aplicación.  
  
     Para crear el botón **Imprimir**, arrastre una herramienta de botón al panel.  
  
     En la ventana **Propiedades**, cambie la propiedad **ID** a **ID\_FILE\_PRINT**, que ya debe estar definida.  Cambie **Caption** a `Imprimir`.  Cambie **Image Index** a `4`.  
  
     Para crear el botón **Impresión rápida**, haga clic en la columna de valor de propiedad que se encuentra al lado de **Elementos de menú** y haga clic en los puntos suspensivos \(**...**\).  En el **Editor de elementos**, haga clic en el botón sin etiqueta **Agregar** para crear un elemento de menú.  En la ventana **Propiedades**, cambie **Caption** a `Impresión rápida`, **ID** a `ID_FILE_PRINT_DIRECT` e **Image** a `5`.  La propiedad Image especifica el icono de impresión rápida en el recurso de mapa de bits IDB\_FILESMALL.  
  
3.  Para comprobar que los botones se agregaron al panel de la cinta, compile la aplicación y ejecútela.  Para compilar la aplicación, en el menú **Generar**, haga clic en **Generar solución**.  Si la aplicación se compila correctamente, haga clic en **Iniciar depuración** en el menú **Depurar** para ejecutarla.  Deberían mostrarse el botón **Imprimir** y el cuadro combinado del panel **Favoritos** en la pestaña **Personalizado** de la cinta.  
  
## Pasos siguientes  
 [Cómo: Personalizar la barra de herramientas de acceso rápido](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
 [Cómo: Personalizar el botón Aplicación](../mfc/how-to-customize-the-application-button.md)  
  
 Para obtener ejemplos de un extremo a otro, vea [Ejemplos \(MFC Feature Pack\)](../top/visual-cpp-samples.md).  
  
## Vea también  
 [Tutoriales](../mfc/walkthroughs-mfc.md)   
 [Ejemplos \(MFC Feature Pack\)](../top/visual-cpp-samples.md)