# Re-learn IC(Internet Computer)

インターネットコンピュータ（IC）は、世界中に分散したデータセンター、ノードマシン、ノード、サブネット、キャニスター、インターネットアイデンティティ、ICPトークンなどの要素が協調して動作する、革新的なブロックチェーンベースのコンピューティングプラットフォームである。

## インターネットコンピュータ（IC）の構成要素

### ICの物理的な構成要素

1.  **データセンター:** ICPの心臓部であるデータセンターは、世界中に分散配置され、ICPの運用に必要な**ノードマシン**を収容する物理的な施設。データセンターは、耐障害性と地理的な冗長性を確保するために、複数の場所に設置される。
2.  **ノードマシン:** ノードマシンは、データセンターに設置された物理的なサーバーコンピュータであり、ICPの頭脳である**ノード**を実行するためのハードウェアを提供する。各ノードマシンは、ICPプロトコルを実行するソフトウェアと、キャニスターの状態やデータを保存するストレージを備えている。
3.  **ノードプロバイダー:** ノードプロバイダーは、ICPネットワークにノードマシンを提供し、運用と保守を担当する組織（人）である。彼らは、データセンターとの契約を通じて、安定したノードマシンの稼働を保証し、ICPネットワークの安定性と信頼性に貢献する。

データセンター、ノードマシン、ノードプロバイダーの数は[Dashboard](https://dashboard.internetcomputer.org/)で確認できる

### ICを構成するソフトウェア

4.  **ノード:** ノードは、ノードマシン上で実行されるソフトウェアであり、ICPの様々な機能を実現する。各ノードは、特定の役割を持つサブネットに所属し、他のノードと協調して動作する。ノードの主な役割には、以下のようなものがある。

    *   **メッセージのルーティング:** ユーザーや他のキャニスターからのメッセージを適切な宛先に転送する。
        <details>
        <summary>メッセージとは？</summary>
        
        インターネットコンピュータ（IC）における「メッセージ」は、**キャニスター間の通信や、ユーザーとキャニスター間のインタラクションを実現するための基本的な仕組み**である。  ICは、従来のブロックチェーンとは異なり、**アクターモデル**を採用しており、トランザクションではなく、メッセージを使用して通信を行う。
        
          <details>
          <summary>アクターモデルとは？</summary>
          
          アクターモデルは、並行処理や分散システムを構築するための計算モデルの一つ。**「アクター」と呼ばれる独立した計算ユニットがメッセージをやり取りすることによって、システム全体が動作する。** 従来のオブジェクト指向プログラミングとは異なり、アクターは内部状態を隠蔽し、メッセージのやり取りを通じてのみ他のアクターと通信する。
          
          **アクターモデルの特徴**
          
          * **並行性**: 複数のアクターは、互いに独立して並行に動作することができる。
          * **メッセージパッシング**: アクター間の通信は、メッセージの送受信によって行われる。直接的なメモリアクセスや共有メモリは使用されない。
          * **非同期性**: メッセージの送受信は非同期に行われる。送信アクターはメッセージを送信後、処理を継続し、受信アクターはメッセージを受信するまで待機する。
          * **状態の独立性**: 各アクターは自身の状態を持ち、他のアクターの状態に直接アクセスすることはできない。
          * **ロケーションの透過性**: アクターは、同一マシン内でも、異なるマシン上でも、透過的に通信することができる。
          
          **インターネットコンピュータ（IC）におけるアクターモデル**
          
          ICは、このアクターモデルを基盤として設計されている。ICにおける「キャニスター」はアクターとして動作し、メッセージのやり取りを通じて互いに通信したり、ユーザーからのリクエストに応答したりする。
          
          **アクターモデルのメリット**
          
          * **複雑なシステムのモデリング**: アクターモデルは、複雑なシステムを、独立したアクターの集合として表現することができる。
          * **並行処理の簡素化**: メッセージパッシングと非同期性により、並行処理プログラムを書きやすくなる。
          * **耐障害性**: アクターは独立して動作するため、一部のアクターに障害が発生しても、システム全体が停止することはない。
          * **スケーラビリティ**: アクターは分散配置が可能であるため、システムの負荷に応じてアクターを追加することで、容易にスケールアウトできる。
          
          **アクターモデルのまとめ**
          
          アクターモデルは、並行処理や分散システムを構築するための強力な計算モデルである。ICは、アクターモデルを採用することで、安全でスケーラブル、かつ柔軟なインターネット基盤を実現している。
  
          </details>
        
        **メッセージの種類**
        
        ICでは、様々な種類のメッセージが使用される。主な種類は以下の通り。
        
        *   **更新メッセージ（Update message）**: キャニスターの状態を変更するために使用される。
        *   **クエリメッセージ（Query message）**: キャニスターの状態を読み取るために使用される。
        *   **応答メッセージ（Response message）**: 更新メッセージやクエリメッセージに対する応答として使用される。
        *   **イングレスメッセージ（Ingress message）**: 外部ユーザーからキャニスターに送信されるメッセージ。ICとユーザーインタラクションの最初のエントリーポイント。
        
        **メッセージの構造**
        
        メッセージは、以下のような構造を持っている。
        
        *   **送信元**: メッセージの送信元となるキャニスターまたはユーザーのID。
        *   **宛先**: メッセージの宛先となるキャニスターのID。
        *   **メソッド名**: 呼び出されるキャニスターのメソッド名。
        *   **引数**: メソッドに渡される引数。
        *   **転送されたCycles**: メッセージに添付されたCycles数。Cyclesは、ICの計算リソースの単位。
        
        **メッセージの処理**
        
        メッセージは、ICのメッセージルーティングシステムによって処理される。メッセージルーティングシステムは、メッセージを適切なキャニスターに配信し、実行を管理する。
        
        **メッセージの保証**
        
        ICは、メッセージの配信と実行に関する以下の保証を提供する。
        
        *   **配信保証**: メッセージは、宛先のキャニスターに確実に配信される。
        *   **順序保証**: 同じ送信元から同じ宛先に送信されたメッセージは、送信された順序で処理される。
        *   **重複排除**: 同じメッセージが複数回配信されることはない。
        
        これらの保証により、ICは、安全で信頼性の高いメッセージングシステムを提供している。
        
        **メッセージとトランザクションの違い**
        
        従来のブロックチェーンでは、トランザクションはアトミックに実行されます。つまり、トランザクション内のすべての操作が成功するか、すべてが失敗するかのいずれかである。一方、ICのメッセージは、アトミックではない。メッセージ内の個々の操作は、他の操作とは独立して成功または失敗する可能性がある。このため、ICの開発者は、メッセージの非アトミックな性質を考慮して、アプリケーションを設計する必要がある。（引用元：[Network Overview - Messages](https://internetcomputer.org/docs/current/developer-docs/getting-started/network-overview#messages)）
        
        **例**
        
        ユーザーがIC上で動作する分散型アプリケーション（dapp）と対話する場合、ユーザーのブラウザは、dappのキャニスターにイングレスメッセージを送信します。イングレスメッセージには、ユーザーが実行したい操作と、その操作に必要なデータが含まれています。キャニスターは、イングレスメッセージを受信すると、その内容に従って処理を実行し、応答メッセージを返します。応答メッセージには、操作の結果や、発生したエラーに関する情報が含まれています。
        
        **「メッセージ」のまとめ**
        
        ICのメッセージは、キャニスター間の通信や、ユーザーとキャニスター間のインタラクションを実現するための基本的な仕組み。メッセージは、ICの分散型アーキテクチャとアクターモデルをサポートし、安全で信頼性の高いメッセージングシステムを提供している。
        </details>
    
    *   **コンセンサス形成:** メッセージの検証やブロックの生成など、ネットワーク全体の合意形成プロセスに参加する。
    *   **キャニスターの実行:** キャニスターのコードを実行し、状態の更新やデータの処理を行う。
    *   **ステートの同期:** 他のノードと状態情報を交換し、ネットワーク全体で最新の状態を維持する。
5.  **サブネット:** サブネットは、複数のノードが連携して動作するグループであり、特定の役割を担う**ノードのチーム**である。ICPでは、以下のような種類のサブネットが存在する。

   * **Application サブネット**
   
      *   **最も一般的なサブネットタイプ**で、**ほとんどすべてのキャニスターがApplication サブネット上で実行**される。
      *   **ユーザーが開発したアプリケーション（dApps）をホストするため**に設計されている。
      *   dAppsを構築するための**スマートコントラクト（キャニスター）はApplication サブネットにデプロイ**される。
      *   Application サブネットは、**個別に設定**することができ、**Bitcoin統合サブネットなど、特定の機能を有効または無効**にすることができる。
      *   Application サブネットは13以上のノードで構成される。
      *   **サブネットの数が増えることで、インターネットコンピュータ全体の容量とスループットが向上**する。
   
   * **System サブネット**
   
      *   **インターネットコンピュータのシステム機能を提供するキャニスターを実行するため**に確保されている。
      *   例えば、**Network Nervous System（NNS）キャニスターは、System サブネット上で実行**されている。
      *   **NNSは、インターネットコンピュータのガバナンスシステム**であり、ノードの追加、サブネットの作成、プロトコルのアップグレードなど、ネットワークのあらゆる側面を制御する。
      *   System サブネットは、**他のサブネットよりも高いセキュリティと信頼性**を備えている必要がある。
          *   System サブネットで実行されるキャニスターはCyclesを必要としない。
          *   また、System サブネットでは、**呼び出しあたりの命令制限とWasmモジュールサイズ制限が、他のサブネットよりも緩和**されている。
      *   [uzr34](https://dashboard.internetcomputer.org/subnet/uzr34-akd3s-xrdag-3ql62-ocgoh-ld2ao-tamcv-54e7j-krwgb-2gm4z-oqe)というサブネットは、31個（2025/01/13現在）のノードで構成されるSystem サブネットの1つ。
          *   このサブネットには、**Internet Identity、Cyclesの台帳、交換レートキャニスター、ダッシュボードのキャニスターがホスト**され、**バックアップのしきい値署名キーも保存**されている。`threshold signature (tECDSA and tSchnorr) signing keys`
   
   * **Fiduciary サブネット**
   
      *   **13ノードよりも大きいサブネット**。
      *   この大規模サブネットで実行されるキャニスターは、**13ノードサブネットで実行されるキャニスターよりも多くのCyclesを支払う**ことになるが、**サブネットのサイズが大きいため、より高いレベルのセキュリティ**が提供されている。
      *   **Fiduciary サブネットタイプは、13ノードサブネットが提供できる保証よりもさらに強力な保証を必要とするDeFiアプリケーションの安全なデプロイを可能にするために作成**された。
      *   [pzp6e](https://dashboard.internetcomputer.org/subnet/pzp6e-ekpqk-3c5x7-2h6so-njoeq-mt45d-h3h6c-q3mxf-vpeq5-fk5o7-yae)というサブネットは、31個のノードを含むFiduciary サブネット。
          *   このサブネットは、**EVM RPCキャニスターをホスト**し、**しきい値署名（tECDSAおよびtSchnorr）署名キーを保存**している。
      *   `dfx ledger create-canister --Subnet-type fiduciary`コマンドを使用して、Fiduciary サブネットにキャニスターをデプロイできる。
   
   * **The European サブネット**
   
      *   **ヨーロッパ地域に配置されたノードマシンのみで構成**されている。
      *   このサブネットタイプにより、開発者や企業は、**GDPRに準拠したインフラストラクチャを必要とするアプリケーションを構築**し、**地域データ主権のニーズに対応しながらブロックチェーンの分散化を活用**できる。
         <details>
         <summary>GDPR（EU一般データ保護規則）とは？</summary>
            「EU一般データ保護規則」（GDPR：General Data Protection Regulation）とは、個人データ保護やその取り扱いについて詳細に定められたEU域内の各国に適用される法令のことで、2018年5月25日に施行された。自然人の基本的な権利の保護という観点から、個人情報の扱いについて規制を行っている。GDPR以前のEUデータ保護指令からさらに厳格化されており、具体的に重要な規制は以下のような事項。

            * 本人が自身の個人データの削除を個人データの管理者に要求できる
            * 自身の個人データを簡単に取得でき、別のサービスに再利用できる（データポータビリティ）
            * 個人データの侵害を迅速に知ることができる
            * 個人データの管理者は個人データ侵害に気付いたときから72時間以内に、規制当局へ当該個人データ侵害を通知することが求められ、また、将来的には本人への報告も求められる。
            * サービスやシステムはデータ保護の観点で設計され、データ保護されることを基本概念とする
            * 法令違反時の罰則強化
            * 監視、暗号化、匿名化などのセキュリティ要件の明確化
            GDPRの特徴は、規制に違反したときに多額の制裁金が課せられること。EU居住者の個人データを取り扱う場合、EUで活動する企業だけではなく、企業規模に関わらず、EU域外の企業にも対応が求められている。
         </details>
      *   European サブネットを利用することで、アプリケーションをGDPRに準拠させることができるが、**開発者と企業は、アプリケーションがすべてのGDPR要件を満たしていることを保証するために、さらなる対策を講じる必要**がある。
      *   `dfx ledger --network ic show-Subnet-types`コマンドを使用すると、**dfxを使用してすべてのサブネットタイプのリスト**を取得できる。
   
   
   これらのサブネットは、ICの多様なニーズに対応し、セキュリティ、スケーラビリティ、信頼性を確保するために重要な役割を果たす。

6.  **キャニスター:** キャニスターは、インターネットコンピュータ上で実行されるスマートコントラクト**。dAppsを構築するための基本的なビルディングブロックであり、**永続的な状態とロジック**を持つ。

   *   **WebAssembly（Wasm）**で記述され、インターネットコンピュータの仮想マシン上で実行される。
   *   **相互に通信**したり、**外部サービスと統合**したりできる。
   *   **データの保存、計算の実行、ユーザーとの対話**など、さまざまなタスクを実行できる。
   
   **キャニスターの特徴**
   
   *   **分散化**: 複数のノードにレプリケートされ、単一障害点がない。
   *   **セキュリティ**:  改ざん防止機能とアクセス制御メカニズムにより保護されている。
   *   **スケーラビリティ**:  インターネットコンピュータの設計により、高負荷にも対応できる。

7.  **インターネットアイデンティティ:**　**インターネットアイデンティティーは、ユーザーがインターネットコンピュータ上のdAppsに安全にログインするための分散型認証システム**。ユーザーは、**自分のデバイス（ラップトップ、スマートフォンなど）を「アンカー」として使用**して、インターネットアイデンティティーを作成できる。

   **インターネットアイデンティティーは、以下のようなメリット**を提供する。
   
   *   **パスワードレス**:  ユーザーは、パスワードを覚える必要がなく、デバイスの生体認証（パスキー）やPINを使用してログインできる。
   *   **プライバシー保護**:  ユーザーの個人情報は、インターネットアイデンティティーシステムに保存されない。
   *   **セキュリティ**:  公開鍵暗号化を使用して、ユーザーのアイデンティティーを保護する。
   *   **分散化**:  単一障害点がなく、検閲に耐性がある。
   
   **インターネットアイデンティティーは、以下のように機能**する。
   
   1.  ユーザーがdAppにログインしようとすると、dAppはユーザーにインターネットアイデンティティーのリクエストを送信する。
   2.  ユーザーは、自分のデバイスでリクエストを確認し、承認する。
   3.  インターネットアイデンティティーシステムは、ユーザーデバイスの固有暗号化キーペアを使用して、ユーザーに代わって署名を作成する。
   4.  dAppは署名を確認し、ユーザーを認証する。
   
   インターネットアイデンティティーは、UXとセキュリティの両方を向上させる革新的な認証システムである。


8.  **ICPトークン:** ICPトークンは、インターネットコンピュータのネイティブユーティリティトークンであり、ネットワークにおいて3つの主要な役割を果たす。

   1. **ネットワークガバナンスの促進**: ICPトークンは、**ニューロンの作成のためにロック**することができる（ステーキング）。ニューロンは投票によってネットワークガバナンスに参加し、報酬を得ることができる。
   2. **計算のためのCyclesの生成**: ICPトークンは、**「Cycles」に変換できる価値の保存手段**を提供する。Cyclesは、燃料の役割を果たし、使用されると消費される。NNSは、ネットワークのユーザーが常に実質的に一定のコストで新しいCyclesを作成できるように、可変レートでICPトークンをCyclesに変換する。これにより、燃料取得のコストが予測可能になる。
   3. **参加者への報酬**: ネットワークの機能を可能にする重要な役割を果たしている人々に報酬を与え、インセンティブを与えるために、新しいICPトークンを発行する。これには、a)ガバナンスに参加する人への「投票報酬」の提供、b)ネットワークをホストしているノードマシンを運用する人への「ノードプロバイダー報酬」の提供が含まれる。
   
   **Cyclesについて**
   
   *   Cyclesは、インターネットコンピュータ上で**キャニスターを実行するための計算リソース**として使用される。
   *   **ICPトークンをCyclesに変換**することで、開発者はキャニスターを実行することができる。（リバースガスモデル）
   *   **Cyclesは、計算に使用されると消費（バーン）**される。
   *   Cyclesの価値は、**法定通貨のグループ（[XDR](https://internetcomputer.org/docs/current/references/glossary#xdr)）と相関**しており、**計算コストを安定**させるように設計されている。
   
   **ニューロンについて**
   
   *   ニューロンは、**ICPトークンをロックすることで作成**される。
   *   ニューロンは、**ネットワークのガバナンスに参加**し、**提案に投票**することができる。
   *   ニューロンの投票力は、**ロックされたICPトークンの量、設定された溶解遅延の長さ、および「年齢」に比例**する。
   *   ニューロンは、**手動で投票**することも、**他のニューロンに従って自動的に投票**することもできる。
   *   ニューロンは、**投票報酬を獲得**することができる。
   
   ### その他の利用方法
   
   *   **起業家、企業、開発者は、任意のトークンの残高を保持し、関数呼び出しの一部として他のキャニスターにトークンを送信するようにキャニスターをプログラム**できる。
   
   ICPトークンは、インターネットコンピュータのエコシステムにおいて重要な役割を果たしており、ネットワークのガバナンス、計算リソース、および参加者への報酬を提供するために使用さる。

## まとめ： ICPは、分散化、安全性、スケーラビリティを追求した次世代のインターネット基盤

ICPは、従来（Web2）のインターネットアーキテクチャの限界を超え、分散化、安全性、スケーラビリティを追求した次世代のインターネット基盤を目指している。世界中に分散したデータセンター、ノードプロバイダー、ノードマシンが物理的な基盤を提供し、ノード、サブネット、キャニスター、インターネットアイデンティティ、ICPトークンなどのソフトウェア要素が協調して動作することで、革新的な機能とユーザー体験を実現しています。
