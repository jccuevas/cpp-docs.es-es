---
title: 'Tutorial: Crear una aplicación de UWP mediante WRL y Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 272092982c5e9cc57f52043e08c8bd384c43ea96
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031516"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Tutorial: Crear una aplicación de UWP mediante WRL y Media Foundation

> [!NOTE]
> Para las nuevas aplicaciones y componentes para UWP, te recomendamos que uses [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), una nueva proyección de lenguaje C++17 estándar para las API de Windows en tiempo de ejecución. C++/WinRT está disponible en el SDK de Windows 10 a partir de la versión 1803. C++/WinRT se implementa completamente en archivos de encabezado y está diseñado para proporcionarle acceso de primera clase a la API de Windows moderna.

En este tutorial, aprenderá a usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL) para crear una aplicación de la Plataforma universal de Windows (UWP) que use [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

Este ejemplo crea una transformación personalizada de Media Foundation que aplica un efecto de escala de grises a las imágenes capturadas con una cámara web. La aplicación utiliza C++ para definir la transformación personalizada y C# para usar el componente para transformar las imágenes capturadas.

> [!NOTE]
> En lugar de C#, también puede usar JavaScript, Visual Basic o C++ para utilizar el componente de transformación personalizado.

En la mayoría de los casos, puede usar C++/CX para crear Windows Runtime. Sin embargo, a veces tiene que utilizar el WRL. Por ejemplo, al crear una extensión multimedia para Microsoft Media Foundation, debe crear un componente que implemente interfaces COM y Windows Runtime. Dado que C++/CX solo puede crear objetos de Windows Runtime, para crear una extensión multimedia debe usar la WRL porque permite la implementación de interfaces COM y Windows Runtime.

> [!NOTE]
> Aunque este ejemplo de código es largo, muestra el mínimo necesario para crear una transformación útil de Media Foundation. Puede utilizarlo como punto de partida para su propia transformación personalizada. Este ejemplo se adapta del [ejemplo Extensiones](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)multimedia, que utiliza extensiones multimedia para aplicar efectos al vídeo, descodificar vídeo y crear controladores de esquema que producen secuencias multimedia.

## <a name="prerequisites"></a>Requisitos previos

- En Visual Studio 2017 y versiones posteriores, la compatibilidad con UWP es un componente opcional. Para instalarlo, abra el instalador de Visual Studio desde el menú Inicio de Windows y busque la versión de Visual Studio. Elija **Modify (Modificar)** y, a continuación, asegúrese de que el icono **Universal Windows Platform Development (Desarrollo** de plataforma universal de Windows) esté activado. En **Componentes opcionales,** comprueba **Las herramientas de C++ para UWP (v141)** para Visual Studio 2017 o las herramientas de **C++ para UWP (v142)** para Visual Studio 2019. A continuación, compruebe la versión del SDK de Windows que desea usar.

- Experiencia con [Windows Runtime](/uwp/api/).

- Experiencia con COM.

- Una cámara web.

## <a name="key-points"></a>Puntos clave

- Para crear un componente personalizado de Media Foundation, utilice un archivo de definición de lenguaje de definición de interfaz de Microsoft (MIDL) para definir una interfaz, implemente esa interfaz y, a continuación, haga que se pueda activar desde otros componentes.

- Los `namespace` `runtimeclass` atributos y `NTDDI_WIN8`y el valor del atributo [version](/windows/win32/Midl/version) son partes importantes de la definición MIDL para un componente de Media Foundation que utiliza WRL.

- [Microsoft::WRL::RuntimeClass](runtimeclass-class.md) es la clase base para el componente Media Foundation personalizado. El valor de enumeración [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix,](runtimeclasstype-enumeration.md) que se proporciona como argumento de plantilla, marca la clase para su uso como clase de Windows Runtime y como una clase de tiempo de ejecución COM clásica.

- La macro [InspectableClass](inspectableclass-macro.md) implementa la funcionalidad COM básica, como el recuento de referencias y el `QueryInterface` método, y establece el nombre de clase en tiempo de ejecución y el nivel de confianza.

- Utilice la clase Microsoft::WRL::[Module](module-class.md) para implementar funciones de punto de entrada DLL como [DllGetActivationFactory](/windows/win32/winrt/functions), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)y [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Vincule la DLL del componente a runtimeobject.lib. Especifique también [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) en la línea del vinculador para generar metadatos de Windows.

- Usa referencias de proyecto para que los componentes WRL sean accesibles para las aplicaciones para UWP.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Para utilizar la WRL para crear el componente de transformación de escala de grises de Media Foundation

1. En Visual Studio, cree un proyecto de **solución en blanco.** Asigne al proyecto el nombre, por ejemplo, *MediaCapture*.

1. Agregue un proyecto **DLL (Windows universal)** a la solución. Asigne al proyecto el nombre, por ejemplo, *GrayscaleTransform*.

1. Agregue un archivo **Midl File (.idl)** al proyecto. Asigne al archivo el nombre, por ejemplo, *GrayscaleTransform.idl*.

1. Agregue este código a GrayscaleTransform.idl:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Utilice el código siguiente para `pch.h`reemplazar el contenido de:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Agregue un nuevo archivo de encabezado `BufferLock.h`al proyecto, asígnelo el nombre y, a continuación, reemplace el contenido con este código:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`no se utiliza en este ejemplo. Puede quitarlo del proyecto si lo desea.

1. Utilice el código siguiente para `GrayscaleTransform.cpp`reemplazar el contenido de:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Agregue un nuevo archivo de definición `GrayscaleTransform.def`de módulo al proyecto, asígnelo un nombre y, a continuación, agregue este código:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Utilice el código siguiente para `dllmain.cpp`reemplazar el contenido de:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. En el cuadro de diálogo **Páginas** de propiedades del proyecto, establezca las siguientes propiedades **del vinculador.**

   1. En **Entrada**, para el `GrayScaleTransform.def`archivo de **definición**de módulo , especifique .

   1. También **Input**en Input `runtimeobject.lib` `mfuuid.lib`, `mfplat.lib` add , , y a la propiedad **Dependencias adicionales.**

   1. En **Metadatos de Windows**, establezca Generar metadatos de **Windows** en **Sí (/WINMD)**.

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Para usar la WRL, el componente personalizado de Media Foundation desde una aplicación de C.

1. Agregue un nuevo proyecto de aplicación en `MediaCapture` **blanco (Windows universal)** a la solución. Asigne al proyecto el nombre, por ejemplo, *MediaCapture*.

1. En el proyecto **MediaCapture,** agregue `GrayscaleTransform` una referencia al proyecto. Para obtener más información, consulte [Cómo: Agregar o quitar referencias mediante el Administrador](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)de referencias .

1. En `Package.appxmanifest`, en la pestaña **Capacidades,** seleccione **Micrófono** y **Webcam**. Ambas capacidades son necesarias para capturar fotografías con la cámara web.

1. En `MainPage.xaml`, agregue este código al elemento [Grid](/uwp/api/windows.ui.xaml.controls.grid) raíz:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Utilice el código siguiente para `MainPage.xaml.cs`reemplazar el contenido de:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

En la ilustración siguiente se muestra el `MediaCapture app`archivo .

![Aplicación MediaCapture que captura una foto](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Pasos siguientes

En el ejemplo se muestra cómo capturar fotografías con la cámara web predeterminada de una en una. El [ejemplo Extensiones](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) de medios hace más. Muestra cómo enumerar los dispositivos de cámara web y trabajar con controladores de esquema locales, además de mostrar los efectos de medios adicionales que funcionan en fotos individuales y secuencias de vídeo.

## <a name="see-also"></a>Vea también

[Biblioteca de plantillas de Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[Ejemplo de extensiones de medios](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
