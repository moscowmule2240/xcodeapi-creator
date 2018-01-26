# xcodeapi-creator
https://bitbucket.org/Unity-Technologies/xcodeapi の DLL を作る

# 仮想環境
    pyenv virtualenv 2.7.14 xcodeapi
    pyenv local xcodeapi
    pip install --requirement requirements.txt

# リポジトリの取得
    hg clone https://bitbucket.org/Unity-Technologies/xcodeapi
    cd xcodeapi
    hg update -C stable

# DLL 作成
    echo -e "\n[assembly: AssemblyInformationalVersion(\"id: `hg identify --id`\")]" >> Xcode/Properties/AssemblyInfo.cs
    /Applications/Unity2017.3.0p3/Unity.app/Contents/Frameworks/MonoBleedingEdge/bin/mcs -r:/Applications/Unity2017.3.0p3/Unity.app/Contents/MonoBleedingEdge/lib/mono/4.6-api/System.Xml.Linq.dll -target:library -recurse:'Xcode/*.cs' -out:XcodeAPI.dll
