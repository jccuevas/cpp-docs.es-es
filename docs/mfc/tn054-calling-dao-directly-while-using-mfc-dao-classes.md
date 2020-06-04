---
title: 'TN054: Llamar a DAO directamente mientras se usan clases DAO de MFC'
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
ms.openlocfilehash: 0eb9daf156f51ecb4eb1e6fdc721b34878a43351
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303421"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: Llamar a DAO directamente mientras se usan clases DAO de MFC

> [!NOTE]
> DAO se utiliza con bases de datos de Access y se admite a través de Office 2013. DAO 3,6 es la versión final y se considera obsoleta. Los asistentes C++ y el entorno visual no admiten DAO (aunque las clases DAO están incluidas y todavía se pueden utilizar). Microsoft recomienda que use [plantillas de OLE DB](../data/oledb/ole-db-templates.md) u [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para proyectos nuevos. Solo se debe utilizar DAO en el mantenimiento de las aplicaciones existentes.

Al utilizar las clases de base de datos DAO de MFC, puede haber situaciones en las que sea necesario usar DAO directamente. Normalmente, este no es el caso, pero MFC ha proporcionado algunos mecanismos auxiliares para facilitar la realización de llamadas a DAO directas al combinar el uso de las clases MFC con llamadas DAO directas. Realizar llamadas DAO directas a los métodos de un objeto DAO administrado por MFC solo debe requerir unas pocas líneas de código. Si tiene que crear y usar objetos DAO que *no* están administrados por MFC, tendrá que realizar un poco más trabajo llamando `Release` en el objeto. En esta nota técnica se explica cuándo es posible que desee llamar directamente a DAO, lo que pueden hacer las aplicaciones auxiliares de MFC para ayudarle y cómo usar las interfaces OLE de DAO. Por último, en esta nota se proporcionan algunas funciones de ejemplo que muestran cómo llamar directamente a DAO para las características de seguridad de DAO.

## <a name="when-to-make-direct-dao-calls"></a>Cuándo realizar llamadas DAO directas

Las situaciones más comunes para realizar llamadas DAO directas se producen cuando es necesario actualizar las colecciones o cuando se implementan características no incluidas en MFC. La característica más importante que MFC no expone es la seguridad. Si desea implementar características de seguridad, deberá usar los usuarios de DAO y los objetos de grupo (s) directamente. Además de la seguridad, solo hay algunas características DAO que no son compatibles con MFC. Entre ellas se incluyen las características de clonación de conjuntos de registros y replicación de base de datos, así como algunas adiciones a DAO.

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Breve introducción a la implementación de DAO y MFC

El ajuste de DAO de MFC facilita el uso de DAO mediante el control de muchos de los detalles, por lo que no tiene que preocuparse por las pocas cosas. Esto incluye la inicialización de OLE, la creación y administración de los objetos DAO (especialmente los objetos de colección), la comprobación de errores y el suministro de una interfaz fuertemente tipada y más sencilla (sin argumentos **Variant** o `BSTR`). Puede realizar llamadas a DAO directas y seguir aprovechando estas características. Todo lo que debe hacer el código es llamar a `Release` para cualquier objeto creado por llamadas a DAO directas y *no* modificar ninguno de los punteros de interfaz que MFC puede utilizar internamente. Por ejemplo, no modifique el miembro *m_pDAORecordset* de un objeto `CDaoRecordset` abierto a menos que entienda *todas* las consecuencias internas. No obstante, podría usar la interfaz *m_pDAORecordset* para llamar a DAO directamente para obtener la colección Fields. En este caso, no se modificaría el miembro de *m_pDAORecordset* . Basta con llamar a `Release` en el objeto de colección Fields cuando termine con el objeto.

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Descripción de las aplicaciones auxiliares para facilitar las llamadas a DAO

Las aplicaciones auxiliares que se proporcionan para facilitar la llamada a DAO son las mismas que se usan internamente en las clases de base de datos DAO de MFC. Estas aplicaciones auxiliares se usan para comprobar los códigos de retorno al realizar una llamada a DAO directa, registrar la salida de depuración, comprobar los errores esperados y producir las excepciones adecuadas si es necesario. Hay dos funciones auxiliares subyacentes y cuatro macros que se asignan a una de estas dos aplicaciones auxiliares. La mejor explicación sería simplemente leer el código. Vea **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**y **DAO_TRACE** en AFXDAO. H para ver las macros y ver **AfxDaoCheck** y **AfxDaoTrace** en DAOCORE. CPP.

## <a name="using-the-dao-ole-interfaces"></a>Usar las interfaces OLE de DAO

Las interfaces OLE para cada objeto de la jerarquía de objetos DAO se definen en el archivo de encabezado DBDAOINT. H, que se encuentra en el directorio \Archivos de Programa\microsoft Visual Studio .NET 2003 \ VC7\include Estas interfaces proporcionan métodos que le permiten manipular toda la jerarquía DAO.

Para muchos de los métodos de las interfaces de DAO, tendrá que manipular un objeto de `BSTR` (una cadena de prefijo de longitud utilizada en la automatización OLE). Normalmente, el objeto de `BSTR` se encapsula dentro del tipo de datos **Variant** . La clase MFC `COleVariant` hereda del tipo de datos **Variant** . Dependiendo de Si compila el proyecto para ANSI o Unicode, las interfaces de DAO devolverán `BSTR`de ANSI o Unicode. Dos macros, V_BSTR y V_BSTRT, son útiles para garantizar que la interfaz de DAO obtiene el `BSTR` del tipo esperado.

V_BSTR extraerá el miembro *bstrVal* de un `COleVariant`. Esta macro se utiliza normalmente cuando es necesario pasar el contenido de una `COleVariant` a un método de una interfaz de DAO. En el siguiente fragmento de código se muestran las declaraciones y el uso real de dos métodos de la interfaz DAOUser de DAO que aprovechan las ventajas de la macro V_BSTR:

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted DAOUser *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;
DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));
DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

Tenga en cuenta que el argumento `VT_BSTRT` especificado en el constructor `COleVariant` anterior garantiza que habrá un `BSTR` ANSI en el `COleVariant` si se compila una versión ANSI de la aplicación y una `BSTR` Unicode para una versión Unicode de la aplicación. Esto es lo que espera DAO.

La otra macro, V_BSTRT, extraerá un miembro *bstrVal* de ANSI o Unicode de `COleVariant` en función del tipo de compilación (ANSI o Unicode). En el código siguiente se muestra cómo extraer el valor `BSTR` de un `COleVariant` en un `CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

La macro V_BSTRT, junto con otras técnicas para abrir otros tipos que se almacenan en `COleVariant`, se muestra en el ejemplo de DAOVIEW. En concreto, esta traducción se realiza en el método `CCrack::strVARIANT`. Este método, siempre que sea posible, convierte el valor de un `COleVariant` en una instancia de `CString`.

## <a name="simple-example-of-a-direct-call-to-dao"></a>Ejemplo sencillo de una llamada directa a DAO

Pueden surgir situaciones en las que sea necesario actualizar los objetos de colección DAO subyacentes. Normalmente, esto no debería ser necesario, pero es un procedimiento sencillo si es necesario. Un ejemplo de Cuándo es necesario actualizar una colección es cuando se trabaja en un entorno multiusuario con varios usuarios que crean nuevas definiciones de nueva. En este caso, la colección TableDefs podría quedar obsoleta. Para actualizar la colección, solo tiene que llamar al método `Refresh` del objeto de colección en cuestión y comprobar si hay errores:

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

Tenga en cuenta que actualmente todas las interfaces de objetos de colección DAO son detalles de implementación no documentada de las clases de base de datos DAO de MFC.

## <a name="using-dao-directly-for-dao-security-features"></a>Usar DAO directamente para características de seguridad de DAO

Las clases de base de datos DAO de MFC no encapsulan las características de seguridad de DAO. Debe llamar a los métodos de las interfaces DAO para utilizar algunas características de seguridad de DAO. La función siguiente establece la base de datos del sistema y, a continuación, cambia la contraseña del usuario. Esta función llama a tres otras funciones, que se definen posteriormente.

```cpp
void ChangeUserPassword()
{
    // Specify path to the Microsoft Access *// system database
    CString strSystemDB =
        _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

    // Set system database before MFC initilizes DAO
    // NOTE: An MFC module uses only one instance
    // of a DAO database engine object. If you have
    // called a DAO object in your application prior
    // to calling the function below, you must call
    // AfxDaoTerm to destroy the existing database
    // engine object. Otherwise, the database engine
    // object already in use will be reused, and setting
    // a system datbase will have no effect.
    //
    // If you have used a DAO object prior to calling
    // this function it is important that DAO be
    // terminated with AfxDaoTerm since an MFC
    // module only gets one copy of the database engine
    // and that engine will be reused if it hasn't been
    // terminated. In other words, if you do not call
    // AfxDaoTerm and there is currently a database
    // initialized, setting the system database will
    // have no effect.
    SetSystemDB(strSystemDB);

    // User name and password manually added
    // by using Microsoft Access
    CString strUserName = _T("NewUser");
    CString strOldPassword = _T("Password");
    CString strNewPassword = _T("NewPassword");

    // Set default user so that MFC will be able
    // to log in by default using the user name and
    // password from the system database
    SetDefaultUser(strUserName, strOldPassword);

    // Change the password. You should be able to
    // call this function from anywhere in your
    // MFC application
    ChangePassword(strUserName, strOldPassword, strNewPassword);

    // ...
}
```

En los cuatro ejemplos siguientes se muestra cómo:

- Establezca la base de datos DAO del sistema (. Archivo MDW).

- Establezca el usuario y la contraseña predeterminados.

- Cambiar la contraseña de un usuario.

- Cambiar la contraseña de un. Archivo MDB.

### <a name="setting-the-system-database"></a>Establecer la base de datos del sistema

A continuación se muestra una función de ejemplo para establecer la base de datos del sistema que se usará en una aplicación. Se debe llamar a esta función antes de que se realicen otras llamadas DAO.

```cpp
// Set the system database that the
// DAO database engine will use

void SetSystemDB(CString& strSystemMDB)
{
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

    // Initialize DAO for MFC
    AfxDaoInit();
    DAODBEngine* pDBEngine = AfxDaoGetEngine();

    ASSERT(pDBEngine != NULL);

    // Call put_SystemDB method to set the *// system database for DAO engine
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));
}
```

### <a name="setting-the-default-user-and-password"></a>Establecer el usuario y la contraseña predeterminados

Para establecer el usuario y la contraseña predeterminados para una base de datos del sistema, utilice la siguiente función:

```cpp
void SetDefaultUser(CString& strUserName,
    CString& strPassword)
{
    COleVariant varUserName(strUserName, VT_BSTRT);
    COleVariant varPassword(strPassword, VT_BSTRT);

    DAODBEngine* pDBEngine = AfxDaoGetEngine();
    ASSERT(pDBEngine != NULL);

    // Set default user:
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

    // Set default password:
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));
}
```

### <a name="changing-a-users-password"></a>Cambiar la contraseña de un usuario

Para cambiar la contraseña de un usuario, utilice la siguiente función:

```cpp
void ChangePassword(CString &strUserName,
    CString &strOldPassword,
    CString &strNewPassword)
{
    // Create (open) a workspace
    CDaoWorkspace wsp;
    CString strWspName = _T("Temp Workspace");

    wsp.Create(strWspName, strUserName, strOldPassword);
    wsp.Append();

    // Determine how many objects there are *// in the Users collection
    short nUserCount;
    short nCurrentUser;
    DAOUser *pUser = NULL;
    DAOUsers *pUsers = NULL;

    // Side-effect is implicit OLE AddRef()
    // on DAOUser object:
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

    // Side-effect is implicit OLE AddRef()
    // on DAOUsers object
    DAO_CHECK(pUsers->getcount(&nUserCount));

    // Traverse through the list of users
    // and change password for the userid
    // used to create/open the workspace
    for(nCurrentUser = 0; nCurrentUser <nUserCount; nCurrentUser++)
    {
        COleVariant varIndex(nCurrentUser, VT_I2);
        COleVariant varName;

        // Retrieve information for user nCurrentUser
        DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

        // Retrieve name for user nCurrentUser
        DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

        CString strTemp = V_BSTRT(&varName);

        // If there is a match, change the password
        if (strTemp == strUserName)
        {
            COleVariant varOldPwd(strOldPassword, VT_BSTRT);
            COleVariant varNewPwd(strNewPassword, VT_BSTRT);

            DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd),
                V_BSTR(&varNewPwd)));

            TRACE("\t Password is changed\n");
        }
    }
    // Clean up: decrement the usage count
    // on the OLE objects
    pUser->Release();
    pUsers->Release();
    wsp.Close();
}
```

### <a name="changing-the-password-of-an-mdb-file"></a>Cambiar la contraseña de un. Archivo MDB

Para cambiar la contraseña de un. Archivo MDB, utilice la siguiente función:

```cpp
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)
{
    CDaoDatabase db;
    CString strConnect(_T(";pwd="));

    // the database must be opened as exclusive
    // to set a password
    db.Open(pDB, TRUE, FALSE, strConnect + pszOldPassword);

    COleVariant NewPassword(pszNewPassword, VT_BSTRT),
                OldPassword(pszOldPassword, VT_BSTRT);

    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword),
        V_BSTR(&NewPassword)));

    db.Close();
}
```

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
