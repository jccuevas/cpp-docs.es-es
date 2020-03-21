---
title: 'Tutorial: crear una aplicación para UWP mediante WRL y Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 5c6fd2613c34fdecdf9128ed6a5d22d563961939
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079889"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Tutorial: crear una aplicación para UWP mediante WRL y Media Foundation

> [!NOTE]
> En el caso de las nuevas aplicaciones y componentes de UWP, se recomienda usar [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), una nueva proyección de lenguaje estándar de c++ 17 para API de Windows Runtime. C++/WinRT está disponible en el SDK de Windows 10 de la versión 1803 en adelante. C++/WinRT se implementa completamente en los archivos de encabezado y está diseñado para proporcionarle acceso de primera clase a la API moderna de Windows.

En este tutorial, obtendrá información sobre cómo usar la biblioteca de C++ plantillas de Windows Runtime (WRL) para crear una aplicación plataforma universal de Windows (UWP) que use [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

Este ejemplo crea una transformación personalizada de Media Foundation que aplica un efecto de escala de grises a las imágenes capturadas con una cámara web. La aplicación utiliza C++ para definir la transformación personalizada y C# para usar el componente para transformar las imágenes capturadas.

> [!NOTE]
> En lugar de C#, también puede usar JavaScript, Visual Basic o C++ para utilizar el componente de transformación personalizado.

En la mayoría de los casos, C++puede usar/CX para crear Windows Runtime. Sin embargo, a veces es necesario usar la WRL. Por ejemplo, al crear una extensión de medios para Microsoft Media Foundation, debe crear un componente que implemente las interfaces COM y Windows Runtime. Dado C++que/CX solo puede crear objetos Windows Runtime, para crear una extensión multimedia debe usar la WRL porque permite la implementación de interfaces COM y Windows Runtime.

> [!NOTE]
> Aunque este ejemplo de código es largo, muestra el mínimo necesario para crear una transformación útil de Media Foundation. Puede utilizarlo como punto de partida para su propia transformación personalizada. Este ejemplo se adapta desde el [ejemplo de extensiones multimedia](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), que usa extensiones de medios para aplicar efectos al vídeo, descodificar vídeo y crear controladores de esquema que producen flujos multimedia.

## <a name="prerequisites"></a>Prerequisites

- En Visual Studio 2017 y versiones posteriores, la compatibilidad con UWP es un componente opcional. Para instalarlo, abra el Instalador de Visual Studio desde el menú Inicio de Windows y busque su versión de Visual Studio. Elija **modificar** y, a continuación, asegúrese de que está activada la casilla **plataforma universal de Windows desarrollo** . En **componentes opcionales** , consulte  **C++ herramientas para UWP (v141)** para Visual Studio 2017 o  **C++ herramientas para UWP (v142)** para Visual Studio 2019. A continuación, Compruebe la versión del Windows SDK que desea utilizar.

- Experiencia con el [Windows Runtime](/uwp/api/).

- Experiencia con COM.

- Una cámara web.

## <a name="key-points"></a>Puntos clave

- Para crear un componente personalizado de Media Foundation, utilice un archivo de definición de lenguaje de definición de interfaz de Microsoft (MIDL) para definir una interfaz, implemente esa interfaz y, a continuación, haga que se pueda activar desde otros componentes.

- Los atributos `namespace` y `runtimeclass`, y el valor del atributo de [versión](/windows/win32/Midl/version) de `NTDDI_WIN8`son partes importantes de la definición de MIDL para un componente de Media Foundation que usa WRL.

- [Microsoft:: WRL:: RuntimeClass](runtimeclass-class.md) es la clase base para el componente de Media Foundation personalizado. El valor de enumeración [Microsoft:: WRL:: runtimeclasstype (:: WinRtClassicComMix](runtimeclasstype-enumeration.md) , que se proporciona como un argumento de plantilla, marca la clase para su uso como una clase Windows Runtime y como una clase en tiempo de ejecución com clásica.

- La macro [inspectableclass (](inspectableclass-macro.md) implementa la funcionalidad básica de com, como el recuento de referencias y el método `QueryInterface`, y establece el nombre de clase en tiempo de ejecución y el nivel de confianza.

- Use la clase Microsoft:: WRL::[Module](module-class.md) para implementar funciones de punto de entrada de dll como [DllGetActivationFactory](/windows/win32/winrt/functions), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)y [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Vincule la DLL del componente a runtimeobject.lib. Especifique también [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) en la línea del vinculador para generar los metadatos de Windows.

- Use referencias de proyecto para hacer que los componentes de WRL estén accesibles para las aplicaciones UWP.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Para usar la WRL para crear el componente de transformación de escala de grises Media Foundation

1. En Visual Studio, cree un proyecto de **solución en blanco** . Asigne un nombre al proyecto, por ejemplo, *MediaCapture*.

1. Agregue un proyecto **dll (universal de Windows)** a la solución. Asigne un nombre al proyecto, por ejemplo, *GrayscaleTransform*.

1. Agregue un archivo de **archivo MIDL (. idl)** al proyecto. Asigne un nombre al archivo, por ejemplo, *GrayscaleTransform. idl*.

1. Agregue este código a GrayscaleTransform. idl:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Use el código siguiente para reemplazar el contenido de `pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Agregue un nuevo archivo de encabezado al proyecto, asígnele el nombre `BufferLock.h`y, a continuación, reemplace el contenido por este código:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h` no se usa en este ejemplo. Puede quitarlo del proyecto si lo desea.

1. Use el código siguiente para reemplazar el contenido de `GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Agregue un nuevo archivo de definición de módulo al proyecto, asígnele el nombre `GrayscaleTransform.def`y, a continuación, agregue este código:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Use el código siguiente para reemplazar el contenido de `dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. En el cuadro de diálogo **páginas de propiedades** del proyecto, establezca las siguientes propiedades del **enlazador** .

   1. En **Input**, para el **archivo de definición de módulo**, especifique `GrayScaleTransform.def`.

   1. También en **entrada**, agregue `runtimeobject.lib`, `mfuuid.lib`y `mfplat.lib` a la propiedad **dependencias adicionales** .

   1. En **metadatos de Windows**, establezca **generar metadatos de Windows** en **sí (/WINMD)** .

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Para usar el componente Media Foundation personalizado de una C# aplicación

1. Agregue un nuevo  **C# proyecto aplicación vacía (Windows universal)** a la solución `MediaCapture`. Asigne un nombre al proyecto, por ejemplo, *MediaCapture*.

1. En el proyecto **MediaCapture** , agregue una referencia al proyecto `GrayscaleTransform`. Para obtener información sobre cómo hacerlo, consulte [Cómo: agregar o quitar referencias mediante el administrador de referencias](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. En `Package.appxmanifest`, en la pestaña **capacidades** , seleccione **micrófono** y **cámara web**. Ambas capacidades son necesarias para capturar fotografías con la cámara web.

1. En `MainPage.xaml`, agregue este código al elemento [Grid](/uwp/api/Windows.UI.Xaml.Controls.Grid) raíz:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Use el código siguiente para reemplazar el contenido de `MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

En la ilustración siguiente se muestra el `MediaCapture app`.

![Aplicación MediaCapture que captura una foto](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Pasos siguientes

En el ejemplo se muestra cómo capturar fotografías con la cámara web predeterminada de una en una. El [ejemplo de extensiones multimedia](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) hace más cosas. Muestra cómo enumerar los dispositivos de cámara web y trabajar con controladores de esquema locales, además de mostrar los efectos de medios adicionales que funcionan en fotos individuales y secuencias de vídeo.

## <a name="see-also"></a>Consulte también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[Ejemplo de extensiones multimedia](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
