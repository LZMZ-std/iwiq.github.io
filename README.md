# iwiq.github.io

<!DOCTYPE html>
<html lang="ru">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <title>VAR / tty0</title>
    <!-- Оформление консоли и встроенного редактора. Все стили находятся здесь. -->
    <style>
      :root {
        color-scheme: dark;
        --bg: #080b0a;
        --fg: #bec8bc;
        --muted: #667367;
        --green: #a4c99b;
        --red: #d28477;
        --amber: #cab084;
      }
      * {
        box-sizing: border-box;
      }
      html,
      body {
        height: 100%;
        margin: 0;
        background: var(--bg);
        color: var(--fg);
        font:
          15px/1.55 Consolas,
          "Courier New",
          monospace;
      }
      body {
        overflow: hidden;
      }
      main {
        height: 100%;
        display: flex;
        flex-direction: column;
        padding: 0 25px;
        background: radial-gradient(ellipse at 50% 50%, #131c1333, transparent 75%);
      }
      header {
        height: 39px;
        flex-shrink: 0;
        display: flex;
        align-items: center;
        justify-content: space-between;
        border-bottom: 1px solid #263024;
        font-size: 11px;
        letter-spacing: 1px;
        color: var(--muted);
      }
      header strong {
        font-weight: normal;
        color: #99a78e;
      }
      #terminal {
        flex: 1;
        min-height: 0;
        display: flex;
        flex-direction: column;
      }
      #output {
        flex: 1;
        min-height: 0;
        overflow: auto;
        padding: 21px 0 10px;
        scrollbar-width: thin;
        scrollbar-color: #303b2f var(--bg);
      }
      .line {
        min-height: 1.55em;
        white-space: pre-wrap;
        overflow-wrap: anywhere;
      }
      .dim {
        color: var(--muted);
      }
      .ok {
        color: var(--green);
      }
      .err {
        color: var(--red);
      }
      .warn {
        color: var(--amber);
      }
      .command {
        color: #d3d9cd;
        margin-top: 11px;
      }
      .form {
        display: flex;
        gap: 9px;
        padding: 9px 0 19px;
        align-items: baseline;
      }
      #prompt {
        color: var(--green);
        white-space: nowrap;
      }
      #input {
        flex: 1;
        min-width: 0;
        font: inherit;
        color: var(--fg);
        background: transparent;
        border: 0;
        padding: 0;
        outline: 0;
        caret-color: #d6e4bf;
      }
      #input:focus-visible {
        box-shadow: 0 1px #283825;
      }
      #editor {
        display: none;
        flex: 1;
        min-height: 0;
        flex-direction: column;
        padding: 15px 0;
      }
      .editor-title {
        padding: 0 0 12px;
        font-size: 12px;
        display: flex;
        justify-content: space-between;
        color: var(--muted);
      }
      .editor-body {
        flex: 1;
        min-height: 0;
        display: flex;
        gap: 18px;
        position: relative;
      }
      #numbers {
        font: inherit;
        line-height: 1.55;
        color: #485645;
        text-align: right;
        padding: 0 8px;
        white-space: pre;
        margin: 0;
        overflow: hidden;
        user-select: none;
      }
      #source {
        flex: 1;
        width: 100%;
        min-width: 0;
        resize: none;
        font: inherit;
        line-height: 1.55;
        color: #c8d6bf;
        background: none;
        border: 0;
        outline: none;
        padding: 0;
        tab-size: 2;
        white-space: pre;
        overflow: auto;
        caret-color: var(--green);
        scrollbar-width: thin;
        scrollbar-color: #303b2f var(--bg);
      }
      #editState {
        color: var(--green);
      }
      main:after {
        content: "";
        position: fixed;
        inset: 0;
        pointer-events: none;
        background: repeating-linear-gradient(transparent 0, transparent 3px, #00000010 4px);
      }
      @media (max-width: 600px) {
        html,
        body {
          font-size: 12px;
        }
        main {
          padding: 0 12px;
        }
        header {
          font-size: 9px;
        }
        header span {
          display: none;
        }
        .form {
          flex-wrap: wrap;
          gap: 2px;
        }
        #input {
          flex-basis: 100%;
        }
        .editor-body {
          gap: 8px;
        }
      }
      @media (prefers-reduced-motion: reduce) {
        main:after {
          display: none;
        }
      }
      .form {
        padding-bottom: 5px;
      }
      @media (max-width: 600px) {
      }
          :root {
        --bg: #080e0d;
        --fg: #d1d9ce;
        --muted: #74877b;
        --green: #b5e5a8;
        --red: #e28c79;
        --amber: #e1bd7c;
        --edge: #24372d;
        --screen: #0a1210;
      }
      body { background: #080e0d; }
      main { max-width:1440px;margin:0 auto;padding:0 40px;background:radial-gradient(ellipse at 24% 35%,#18261c35,transparent 58%); }
      header { height:58px;border-bottom-color:var(--edge);letter-spacing:.4px;position:relative; }
      header:after {content:"";position:absolute;bottom:-1px;left:0;width:138px;height:1px;background:linear-gradient(90deg,var(--green),transparent)}
      .brand,.connection {display:flex;align-items:center}.brand{gap:11px}
      .brand-mark {display:grid;place-items:center;width:29px;height:29px;border:1px solid #3d5946;border-radius:5px;background:#122018;color:var(--green);font-weight:bold;font-size:16px}
      .brand strong{font-size:11px;letter-spacing:1.4px;color:#cfdbca}.brand strong i{font-style:normal;color:#63786a}
      .brand small{display:block;margin-top:3px;font-size:8px;letter-spacing:1.3px;color:#637469}
      .connection{gap:9px;font-size:10px;color:#9aa99a}
      #led{width:6px;height:6px;border-radius:50%;background:#86927d;box-shadow:0 0 7px #86927d66}
      .is-connected #led{background:var(--green);box-shadow:0 0 9px #a9f390aa}
      #terminal{position:relative}
      #output{padding:28px 18px 18px;border-left:1px solid #18261e;border-right:1px solid #18261e;background:linear-gradient(90deg,#080e0d,#0a100e 12%,#0a100e 88%,#080e0d);scrollbar-color:#314333 var(--screen)}
      #output:before{content:"SYSTEM CONSOLE  /  SECURE SHELL";display:block;margin-bottom:18px;padding-bottom:10px;border-bottom:1px solid #1d2b22;color:#627467;font-size:9px;letter-spacing:1.4px}
      .line{line-height:1.65}.command{margin-top:14px;color:#e0e8dc}
      .form{gap:12px;align-items:center;padding:14px 18px 13px;border:1px solid #304936;border-top-color:#456349;border-radius:3px;background:#101a13;box-shadow:0 0 22px #94cf7610,inset 0 1px #d0f4a40a}
      #prompt{color:#b8e7a8;text-shadow:0 0 9px #9dda8a44}#input{color:#e0e8dc}#input:focus-visible{box-shadow:none}
      .statusbar{height:29px;display:flex;justify-content:space-between;align-items:center;padding:0 3px;color:#65766b;font-size:9px;letter-spacing:.4px}
      .statusbar b{font-weight:normal;color:#93a68f}#linkstate{color:#86947e}.is-connected #linkstate{color:var(--green)}
      .dim{color:#819083}.ok{color:#b5e5a8}.err{color:#e28c79}.warn{color:#e1bd7c}
      #editor{border:1px solid #23342a;border-radius:3px;margin-top:17px;padding:16px;background:#0b120e}
      .editor-title{border-bottom:1px solid #1d2b22;padding-bottom:11px}#source{color:#d1dec9}#numbers{color:#526652}
      @media(max-width:700px){main{padding:0 12px}header{height:50px}.brand small{font-size:7px}.connection{font-size:9px}#output{padding:19px 10px 12px}.statusbar{font-size:8px}#editor{padding:12px 8px}}
      @media(min-width:1100px){main{padding-left:clamp(35px,7vw,110px);padding-right:clamp(35px,7vw,110px)}#output{padding-top:36px}}

</style>
  </head>
  <body>
    <!-- Интерфейс: заголовок, журнал консоли, строка ввода и редактор кода. -->
    <main>
      <header><div class="brand"><span class="brand-mark">V</span><div><strong>VAR <i>/</i> FIELD SYSTEMS</strong><small>SECURE ACCESS TERMINAL · REV 1.1</small></div></div><div class="connection"><span id="led"></span><span id="tty">tty0 · local</span></div></header>
      <section id="terminal" aria-label="Консоль датапада">
        <div id="output" role="log" aria-live="polite" aria-relevant="additions" tabindex="0"></div>
        <form class="form" id="form" autocomplete="off">
          <label id="prompt" for="input"></label
          ><input
            id="input"
            aria-label="Командная строка"
            spellcheck="false"
            autocomplete="off"
            autocapitalize="off"
            maxlength="1024"
            autofocus
          />
        </form>
        <div class="statusbar"><span><b>SESSION</b> &nbsp;LOCAL / 1.1</span><span id="linkstate">DATAPAD ATTACHED</span><span>INPUT &nbsp;READY</span></div>
      </section>
      <section id="editor" aria-label="Редактор исходного кода">
        <div class="editor-title"><span id="editPath"></span><span id="editState"></span></div>
        <div class="editor-body">
          <pre id="numbers" aria-hidden="true">1</pre>
          <textarea
            id="source"
            aria-label="Исходный код"
            spellcheck="false"
            autocomplete="off"
            autocapitalize="off"
            wrap="off"
          ></textarea>
        </div>
      </section>
    </main>
    <script>
      (function () {
        "use strict";
        /*
         * Игровая консоль уровня 1.1. CSS и JavaScript встроены в этот HTML.
         *
         * /datapad — локальные программы и сохранённые данные игрока.
         * /cis — файловая система терминала, доступная после подключения.
         *
         * Все команды работают с виртуальными файлами внутри страницы.
         * Роллы и бонус инженера вычисляются скрыто: в консоль они не выводятся.
         *
         * Мост для мода: window.KNSHack.getState(), reset(), setRole(), setNextRoll().
         * События window "kns-hack" передают тип события, данные и состояние сессии.
         * Событие "completed" означает, что файл скопирован на датапад.
         * Событие "disconnected" означает, что игрок закрыл соединение.
         */

        // Элементы интерфейса и состояние текущей сессии.
        var $ = function (id) {
            return document.getElementById(id);
          },
          out = $("output"),
          input = $("input"),
          source = $("source");
        var fs = {},
          cwd = "/datapad",
          connected = false,
          discovered = false,
          located = false,
          completed = false,
          role = "standard",
          nextRoll = null,
          lastRoll = null,
          port = "",
          target = "",
          secret = "",
          busy = false,
          epoch = 0,
          session = 0,
          history = [],
          hi = 0,
          draft = "",
          editing = null,
          dirty = false,
          editorOriginal = "",
          rollUsed = false;
        var moduleReady = false,
          keyRecovered = false,
          keySeed = 0,
          attemptLimit = 0,
          matchIndex = 0;

        // Порядок действий для help <уровень>. Другие уровни пока представлены справкой.
        var levelGuides = {
          "1.1": [
            "Обнаружить открытый сервисный порт терминала.",
            "Подключить датапад к обнаруженному порту.",
            "Найти защищённый файл в каталоге консоли.",
            "Выбрать брутфорс на датападе и запустить подбор.",
            "Открыть файл с помощью полученного ключа.",
            "Скопировать нужные данные на датапад.",
            "Отключиться от терминала.",
          ],
          "1.2": [
            "Обнаружить сервисный порт и подключить датапад.",
            "Найти защищённый файл в каталоге консоли.",
            "Выбрать брутфорс и энкриптор на датападе.",
            "Направить результат брутфорса в энкриптор.",
            "Направить обработанный ключ из энкриптора в систему доступа.",
            "Запустить брутфорс и энкриптор. При сбое повторить настройку цепочки и запуск.",
            "Ввести полученный ключ и открыть файл.",
            "Скопировать данные на датапад и отключиться.",
          ],
          "1.3": [
            "Обнаружить сервисный порт и подключить датапад.",
            "Найти защищённый файл в каталоге консоли.",
            "Выбрать брутфорс или мультифорс вместе с энкриптором.",
            "Направить результат подбора в энкриптор.",
            "Направить результат энкриптора в систему доступа.",
            "Запустить цепочку программ. Если текущий ключ сменился, повторить настройку и запуск.",
            "Ввести актуальный ключ и открыть файл.",
            "Скопировать данные на датапад и отключиться.",
          ],
          "2.1": [
            "Обнаружить сервисный порт и подключить датапад.",
            "Найти файл внешней защиты в каталоге консоли.",
            "Запустить брутфорс для файла внешней защиты.",
            "Открыть параметры файла защиты и отключить внешний слой.",
            "Найти нужный защищённый файл внутри архива.",
            "Запустить брутфорс для найденного файла.",
            "Ввести ключ и открыть файл.",
            "Скопировать данные на датапад и отключиться.",
          ],
          "2.2": [
            "Обнаружить сервисный порт и подключить датапад.",
            "Найти файл внешней защиты.",
            "Выбрать брутфорс и энкриптор.",
            "Направить результат брутфорса в энкриптор.",
            "Направить результат энкриптора в файл внешней защиты.",
            "Запустить цепочку. При сбое повторить настройку и запуск.",
            "Открыть параметры файла защиты и отключить внешний слой.",
            "Найти нужный защищённый файл внутри архива.",
            "Перенастроить цепочку на найденный файл и запустить подбор с энкриптором.",
            "Ввести ключ, скопировать данные на датапад и отключиться.",
          ],
          "2.3": [
            "Обнаружить сервисный порт и подключить датапад.",
            "Найти файл внешней защиты.",
            "Выбрать брутфорс или мультифорс вместе с энкриптором.",
            "Направить результат подбора в энкриптор.",
            "Направить результат энкриптора в файл внешней защиты.",
            "Запустить цепочку. Если ключ сменился, повторить настройку и запуск.",
            "Открыть параметры файла защиты и отключить внешний слой.",
            "Найти нужный защищённый файл внутри архива.",
            "Перенастроить цепочку на найденный файл и повторить подбор с энкриптором. При смене ключа повторить запуск.",
            "Ввести актуальный ключ, скопировать данные на датапад и отключиться.",
          ],
        };
        var commands = [
          "disconnect",
          "cat",
          "cd",
          "clear",
          "connect",
          "cp",
          "edit",
          "find",
          "grep",
          "help",
          "ls",
          "ping",
          "pwd",
          "run",
          "stat",
          "status",
          "unlock",
        ];

        // Случайные значения и генерация длинных игровых ключей.
        function rand(max) {
          if (window.crypto && window.crypto.getRandomValues) {
            var a = new Uint32Array(1),
              limit = Math.floor(4294967296 / max) * max;
            do {
              window.crypto.getRandomValues(a);
            } while (a[0] >= limit);
            return a[0] % max;
          }
          return Math.floor(Math.random() * max);
        }
        function candidateCode(index) {
          var value = (Math.imul(index + 1, 2654435761) ^ keySeed) >>> 0,
            hex = value.toString(16).toUpperCase().padStart(8, "0"),
            tail = ((Math.imul(index + 1, 2246822519) ^ keySeed) >>> 16)
              .toString(16)
              .toUpperCase()
              .padStart(4, "0");
          return "CIS-" + hex.slice(0, 4) + "-" + hex.slice(4) + "-" + tail;
        }

        // Состояние и события, которые может получать мод Arma 3.
        function snapshot() {
          return {
            level: "1.1",
            session: session,
            connected: connected,
            discovered: discovered,
            port: discovered ? port : null,
            located: located,
            busy: busy,
            role: role,
            lastRoll: lastRoll ? Object.assign({}, lastRoll) : null,
            completed: completed,
            moduleReady: moduleReady,
            keyRecovered: keyRecovered,
          };
        }
        function emit(type, payload) {
          window.dispatchEvent(
            new CustomEvent("kns-hack", {
              detail: { type: type, payload: payload || {}, state: snapshot() },
            }),
          );
        }

        // Вывод в консоль. Пользовательский текст вставляется как текст, а не HTML.
        function write(text, kind) {
          var el = document.createElement("div");
          el.className = "line " + (kind || "");
          el.textContent = String(text);
          out.appendChild(el);
          while (out.children.length > 700) out.removeChild(out.firstChild);
          out.scrollTop = out.scrollHeight;
          return el;
        }
        function fail(message) {
          throw new Error(message);
        }

        // Виртуальная файловая система: пути, права доступа и чтение файлов.
        function path(value) {
          var raw = value && value[0] === "/" ? value : cwd + "/" + (value || ""),
            parts = [];
          raw.split("/").forEach(function (p) {
            if (!p || p === ".") return;
            if (p === "..") parts.pop();
            else parts.push(p);
          });
          return "/" + parts.join("/");
        }
        function parent(p) {
          return p.slice(0, p.lastIndexOf("/")) || "/";
        }
        function isRemote(p) {
          return p === "/cis" || p.indexOf("/cis/") === 0;
        }
        function item(p) {
          if (isRemote(p) && !connected) fail(p + ": ENOTCONN");
          if (!fs[p]) fail(p + ": ENOENT");
          return fs[p];
        }
        function textFile(p) {
          var f = item(p);
          if (f.dir) fail(p + ": EISDIR");
          if (f.locked) fail(p + ": EACCES");
          return f.text;
        }
        function add(p, text, locked) {
          fs[p] = { text: text, locked: !!locked };
        }
        function dir(p) {
          fs[p] = { dir: true };
        }

        // Строка приглашения показывает текущий каталог и состояние соединения.
        function prompt() {
          $("prompt").textContent = "operator@var-pad:" + cwd + "$";
          $("tty").textContent = "tty0 · " + (connected ? "aux://D-04:" + port : "local");
          document.body.classList.toggle("is-connected", connected);
          $("linkstate").textContent = connected ? "CIS LINK · ESTABLISHED" : "DATAPAD ATTACHED";
        }

        // Скрытая проверка: результат 51+ успешен; у инженера есть бонус +5.
        function roll(label) {
          var raw = nextRoll === null ? rand(101) : nextRoll;
          nextRoll = null;
          var bonus = role === "engineer" ? 5 : 0;
          lastRoll = {
            raw: raw,
            bonus: bonus,
            total: raw + bonus,
            success: raw + bonus >= 51,
            context: label,
          };
          emit("roll", Object.assign({}, lastRoll));
          return lastRoll.success;
        }
        function pause(ms) {
          return new Promise(function (resolve) {
            setTimeout(resolve, ms);
          });
        }
        function live(token) {
          if (token !== epoch) fail("SIGINT");
        }

        // Разбор команды с поддержкой аргументов в кавычках.
        function shellTokens(text) {
          var parts = [],
            re = /"([^"\\]*(?:\\.[^"\\]*)*)"|'([^']*)'|([^\s]+)/g,
            m;
          while ((m = re.exec(text)))
            parts.push(
              m[1] !== undefined
                ? m[1].replace(/\\(["\\])/g, "$1")
                : m[2] !== undefined
                  ? m[2]
                  : m[3],
            );
          if ((text.match(/"/g) || []).length % 2 || (text.match(/'/g) || []).length % 2)
            fail("shell: unterminated string");
          return parts;
        }
        function usage(cmd) {
          var syntax = {
            ping: "ping",
            connect: "connect <номер порта>",
            disconnect: "disconnect",
            ls: "ls [-la] [путь]",
            cd: "cd [каталог]",
            pwd: "pwd",
            cat: "cat <файл>",
            stat: "stat <путь>",
            find: 'find [каталог] [маска] или find [каталог] -name "маска"\nВ текущем каталоге: find "*.dat"',
            grep: "grep <строка> <файл>",
            edit: "edit <файл>",
            run: "run bruteforce <защищённый файл> или run <скрипт>",
            unlock: "unlock <файл> --key <ключ>",
            cp: "cp <источник> <назначение>",
            help: "help [1.1|1.2|1.3|2.1|2.2|2.3]",
            status: "status",
          };
          fail(cmd + ": неверные аргументы\nСинтаксис: " + (syntax[cmd] || cmd));
        }
        function list(p, all) {
          var f = item(p);
          if (!f.dir) return p.split("/").pop();
          var rows = Object.keys(fs)
            .filter(function (x) {
              return x !== "/" && parent(x) === p && (all || x.split("/").pop()[0] !== ".");
            })
            .sort();
          return rows
            .map(function (x) {
              var e = fs[x];
              return (
                (e.dir ? "d" : e.locked ? "-" : "-") +
                (e.dir ? "r-xr-x---" : e.locked ? "---------" : "rw-r-----") +
                "  " +
                String(e.dir ? 0 : e.text.length).padStart(6, " ") +
                "  " +
                x.split("/").pop() +
                (e.dir ? "/" : "")
              );
            })
            .join("\n");
        }
        function writable(p) {
          if (p.indexOf("/datapad/") !== 0) fail(p + ": EROFS");
          if (!item(parent(p)).dir) fail(parent(p) + ": ENOTDIR");
        }

        // Редактор: Ctrl+S сохраняет файл; Escape закрывает сохранённый буфер.
        function openEditor(p) {
          writable(p);
          if (fs[p] && fs[p].dir) fail(p + ": EISDIR");
          editing = p;
          dirty = false;
          editorOriginal = fs[p] ? textFile(p) : "";
          source.value = editorOriginal;
          $("terminal").style.display = "none";
          $("editor").style.display = "flex";
          $("editPath").textContent = p;
          $("editState").textContent = "";
          numbers();
          source.focus();
        }
        function numbers() {
          $("numbers").textContent = source.value
            .split("\n")
            .map(function (_, i) {
              return i + 1;
            })
            .join("\n");
          $("numbers").scrollTop = source.scrollTop;
        }
        function closeEditor() {
          editing = null;
          $("editor").style.display = "none";
          $("terminal").style.display = "flex";
          input.focus();
        }
        // Скрипты поддерживают let/const, for...of, if, break, вызовы функций и сравнения.
        // Это игровой интерпретатор ограниченного набора конструкций JavaScript.

        // Компиляция ограниченного языка скриптов. Здесь проверяется синтаксис.
        function compile(code) {
          var tokens = [],
            pos = 0,
            line = 1;
          while (pos < code.length) {
            var ch = code[pos];
            if (/\s/.test(ch)) {
              if (ch === "\n") line++;
              pos++;
              continue;
            }
            if (code.slice(pos, pos + 2) === "//") {
              while (pos < code.length && code[pos] !== "\n") pos++;
              continue;
            }
            if (code.slice(pos, pos + 2) === "/*") {
              var end = code.indexOf("*/", pos + 2);
              if (end < 0) fail("compile:" + line + ": unterminated comment");
              line += (code.slice(pos, end + 2).match(/\n/g) || []).length;
              pos = end + 2;
              continue;
            }
            var at = line;
            if (ch === '"' || ch === "'") {
              var quote = ch,
                value = "";
              pos++;
              var closed = false;
              while (pos < code.length) {
                ch = code[pos++];
                if (ch === quote) {
                  closed = true;
                  break;
                }
                if (ch === "\n") fail("compile:" + at + ": newline in string");
                if (ch === "\\") {
                  var escape = code[pos++];
                  value +=
                    escape === "n" ? "\n" : escape === "t" ? "\t" : escape === "r" ? "\r" : escape;
                } else value += ch;
              }
              if (!closed) fail("compile:" + at + ": unterminated string");
              tokens.push({ type: "string", value: value, line: at });
              continue;
            }
            var m = code.slice(pos).match(/^[A-Za-z_$][\w$]*/);
            if (m) {
              tokens.push({ type: "id", value: m[0], line: at });
              pos += m[0].length;
              continue;
            }
            m = code.slice(pos).match(/^\d+/);
            if (m) {
              tokens.push({ type: "number", value: Number(m[0]), line: at });
              pos += m[0].length;
              continue;
            }
            m = code.slice(pos).match(/^(===|!==|==|!=|<=|>=|[{}();,=<>!])/);
            if (m) {
              tokens.push({ type: "symbol", value: m[0], line: at });
              pos += m[0].length;
              continue;
            }
            fail("compile:" + line + ": unexpected token " + ch);
          }
          tokens.push({ value: "<eof>", line: line });
          var i = 0;
          function peek() {
            return tokens[i];
          }
          function accept(v) {
            if (peek().value === v) {
              i++;
              return true;
            }
            return false;
          }
          function expect(v) {
            if (!accept(v))
              fail("compile:" + peek().line + ": expected " + v + ", got " + peek().value);
          }
          function identifier() {
            var t = peek();
            if (t.type !== "id") fail("compile:" + t.line + ": expected identifier");
            i++;
            return t.value;
          }
          function expression() {
            var node;
            if (accept("!")) node = { type: "not", value: expression() };
            else if (accept("(")) {
              node = expression();
              expect(")");
            } else {
              var t = peek();
              i++;
              if (t.type === "string" || t.type === "number")
                node = { type: "literal", value: t.value };
              else if (t.value === "true" || t.value === "false")
                node = { type: "literal", value: t.value === "true" };
              else if (t.type === "id") {
                if (accept("(")) {
                  var args = [];
                  if (!accept(")")) {
                    do {
                      args.push(expression());
                    } while (accept(","));
                    expect(")");
                  }
                  node = { type: "call", name: t.value, args: args, line: t.line };
                } else node = { type: "var", name: t.value, line: t.line };
              } else fail("compile:" + t.line + ": expected expression");
            }
            if (["===", "!==", "==", "!=", "<", ">", "<=", ">="].includes(peek().value)) {
              var op = tokens[i++].value;
              node = { type: "compare", op: op, left: node, right: expression() };
            }
            return node;
          }
          function block() {
            expect("{");
            var rows = [];
            while (peek().value !== "}") {
              if (peek().value === "<eof>") fail("compile:" + peek().line + ": expected }");
              rows.push(statement());
            }
            expect("}");
            return rows;
          }
          function statement() {
            var at = peek().line;
            if (accept("let") || accept("const")) {
              var name = identifier();
              expect("=");
              var value = expression();
              expect(";");
              return { type: "let", name: name, value: value, line: at };
            }
            if (accept("for")) {
              expect("(");
              if (!accept("let") && !accept("const"))
                fail("compile:" + at + ": expected loop binding");
              var name = identifier();
              expect("of");
              var value = expression();
              expect(")");
              return { type: "for", name: name, value: value, body: block(), line: at };
            }
            if (accept("if")) {
              expect("(");
              var value = expression();
              expect(")");
              return { type: "if", value: value, body: block(), line: at };
            }
            if (accept("break")) {
              expect(";");
              return { type: "break", line: at };
            }
            var value = expression();
            expect(";");
            return { type: "expr", value: value, line: at };
          }
          var program = [];
          while (peek().value !== "<eof>") program.push(statement());
          return program;
        }

        // Исполнение пользовательского скрипта с лимитом инструкций и прерыванием.
        async function runScript(p, token) {
          var tree = compile(textFile(p)),
            bindings = new Map(),
            ops = 0,
            attempts = 0,
            delay = 100,
            batch = 120,
            progress = null,
            found = false,
            probeSeen = false,
            breakSignal = {};
          write("[vm] " + p + " / loaded " + tree.length + " statements", "dim");
          function step() {
            if (++ops > 90000) fail("vm: instruction limit exceeded");
            live(token);
          }
          async function expr(node) {
            step();
            if (node.type === "literal") return node.value;
            if (node.type === "var") {
              if (!bindings.has(node.name))
                fail("runtime:" + node.line + ": " + node.name + " is not defined");
              return bindings.get(node.name);
            }
            if (node.type === "not") return !(await expr(node.value));
            if (node.type === "compare") {
              var a = await expr(node.left),
                b = await expr(node.right);
              switch (node.op) {
                case "===":
                case "==":
                  return a === b;
                case "!==":
                case "!=":
                  return a !== b;
                case "<":
                  return a < b;
                case ">":
                  return a > b;
                case "<=":
                  return a <= b;
                case ">=":
                  return a >= b;
              }
            }
            if (node.type === "call") {
              var args = [];
              for (var n of node.args) args.push(await expr(n));
              switch (node.name) {
                case "readlines":
                  if (args.length !== 1 || typeof args[0] !== "string") fail("readlines: EINVAL");
                  return textFile(path(args[0])).split(/\r?\n/).filter(Boolean);
                case "print":
                  if (args.length !== 1) fail("print: EINVAL");
                  write(String(args[0]));
                  if (found && args[0] === secret) keyRecovered = true;
                  return undefined;
                case "probe":
                  if (
                    args.length !== 2 ||
                    typeof args[0] !== "string" ||
                    typeof args[1] !== "string"
                  )
                    fail("probe: EINVAL");
                  var fp = path(args[0]);
                  if (!located) fail("probe: target index unresolved");
                  var f = item(fp);
                  if (fp !== target || !f.locked) fail("probe: invalid lock target");
                  if (!probeSeen) {
                    probeSeen = true;
                    var fast = roll("BF-01");
                    batch = fast ? 140 : 45;
                    progress = write("[probe] 0 candidates", "dim");
                  }
                  attempts++;
                  if (attempts % batch === 0) {
                    progress.textContent = "[probe] " + attempts + " candidates / " + args[1];
                    await pause(delay);
                    live(token);
                  }
                  if (args[1] === secret) {
                    found = true;
                    return true;
                  }
                  return false;
                default:
                  fail("runtime:" + node.line + ": unknown function " + node.name);
              }
            }
            fail("vm: invalid expression");
          }
          async function walk(rows, depth) {
            for (var node of rows) {
              step();
              if (node.type === "let") {
                if (bindings.has(node.name))
                  fail("runtime:" + node.line + ": duplicate binding " + node.name);
                bindings.set(node.name, await expr(node.value));
              } else if (node.type === "expr") await expr(node.value);
              else if (node.type === "if") {
                if (await expr(node.value)) await walk(node.body, depth);
              } else if (node.type === "break") {
                if (depth === 0) fail("runtime:" + node.line + ": break outside loop");
                throw breakSignal;
              } else if (node.type === "for") {
                var values = await expr(node.value);
                if (!Array.isArray(values))
                  fail("runtime:" + node.line + ": value is not iterable");
                if (bindings.has(node.name))
                  fail("runtime:" + node.line + ": duplicate loop binding " + node.name);
                try {
                  for (var value of values) {
                    bindings.set(node.name, value);
                    try {
                      await walk(node.body, depth + 1);
                    } catch (e) {
                      if (e === breakSignal) break;
                      throw e;
                    }
                  }
                } finally {
                  bindings.delete(node.name);
                }
              }
            }
          }
          await walk(tree, 0);
          live(token);
          if (progress)
            progress.textContent =
              "[probe] " + attempts + " candidates / " + (found ? "match" : "exhausted");
          write("[vm] exit 0 / " + ops + " instructions", "dim");
          emit("script-finished", { attempts: attempts, matched: found });
        }

        // Обработчики команд shell: справка, подключение, поиск, программы и копирование.
        async function execute(raw) {
          var a = shellTokens(raw),
            cmd = a.shift();
          if (!cmd) return;
          if (cmd === "help") {
            if (a.length) {
              if (a.length !== 1 || !levelGuides[a[0]])
                fail("help: неизвестный уровень. Доступны: " + Object.keys(levelGuides).join(", "));
              write("УРОВЕНЬ " + a[0] + " / ПОРЯДОК ДЕЙСТВИЙ", "dim");
              levelGuides[a[0]].forEach(function (step, i) {
                write(i + 1 + ". " + step);
              });
              if (a[0] !== "1.1")
                write("Справочный сценарий. Текущая консоль работает на уровне 1.1.", "dim");
              return;
            }
            write("VAR shell / commands", "dim");
            write(
              "  ping                         опрос устройства и портов\n  connect <порт>               подключение к сервисному порту\n  disconnect                  завершить соединение\n  ls [-la] [путь]              список файлов\n  cd [каталог]                 смена каталога\n  pwd                          текущий каталог\n  cat <файл>                   чтение файла\n  stat <путь>                  свойства объекта\n  find [каталог] [маска]       поиск; без пути — в текущем каталоге\n  grep <строка> <файл>         поиск строк в файле\n  edit <файл>                  редактор исходного кода\n  run <программа> <файл>      запуск программы с датапада\n  run <скрипт>                 выполнение своего скрипта\n  unlock <файл> --key <ключ>   открытие защищённого файла\n  cp <источник> <назначение>   копирование файла\n  status                       состояние системы\n  clear                        очистка экрана\n  help                         справочник команд\n  help <уровень>               порядок действий: 1.1–2.3",
            );
            write(
              "Каталоги: /datapad — локальный; /cis — консоль после подключения.\nПрограммы: bruteforce, multiforce, encryptor.\nПоиск автоматически повторяется до обнаружения файла.",
              "dim",
            );
            write(
              "Tab — дополнение команд и путей; ↑/↓ — история.\nCtrl+C — прерывание процесса; Ctrl+L — очистка экрана.\nРедактор: Ctrl+S — сохранить; Esc — закрыть сохранённый файл.",
              "dim",
            );
            return;
          }
          if (cmd === "status") {
            if (a.length) usage(cmd);
            write("VAR-PAD / session " + String(session).padStart(3, "0"), "dim");
            write(
              "aux0       carrier detected\nendpoint   " +
                (discovered ? "D-04:" + port : "unresolved") +
                "\nconnection " +
                (connected ? "established" : "closed") +
                "\nvolume     " +
                (connected ? "/cis" : "unmounted") +
                "\ncwd        " +
                cwd +
                "\nprocess    " +
                (busy ? "running" : "idle") +
                "\nindex      " +
                (located ? "resolved" : "unresolved") +
                "\ntransfer   " +
                (completed ? "complete" : "pending"),
            );
            if (located)
              write(
                "target     " +
                  target +
                  "\naccess     " +
                  (fs[target] && !fs[target].locked ? "0640" : "0000 / locked"),
              );
            return;
          }
          if (cmd === "clear" && a.length === 0) {
            out.textContent = "";
            return;
          }
          if (cmd === "disconnect") {
            if (a.length) usage(cmd);
            if (!connected) fail("disconnect: активного соединения нет");
            epoch++;
            busy = false;
            connected = false;
            if (isRemote(cwd)) cwd = "/datapad";
            write("aux0: link closed; /cis unmounted", "dim");
            prompt();
            emit("disconnected", { port: port });
            return;
          }
          if (busy) fail("shell: device busy");
          var token = epoch;
          if (cmd === "pwd") {
            if (a.length) usage(cmd);
            write(cwd);
            return;
          }
          if (cmd === "cd") {
            if (a.length > 1) usage(cmd);
            var p = path(a[0] || "/datapad");
            if (!item(p).dir) fail(p + ": ENOTDIR");
            cwd = p;
            prompt();
            return;
          }
          if (cmd === "ls") {
            var all = false,
              values = [];
            a.forEach(function (x) {
              if (x === "-a" || x === "-la" || x === "-al") all = true;
              else if (x !== "-l") values.push(x);
            });
            if (values.length > 1) usage(cmd);
            var listing = list(path(values[0] || cwd), all);
            if (listing) write(listing);
            else write("Видимых файлов нет. Скрытые файлы: ls -la. Все каталоги: ls /", "dim");
            return;
          }
          if (cmd === "cat") {
            if (a.length !== 1) usage(cmd);
            write(textFile(path(a[0])));
            return;
          }
          if (cmd === "stat") {
            if (a.length !== 1) usage(cmd);
            var p = path(a[0]),
              f = item(p);
            write(
              "File: " +
                p +
                "\nType: " +
                (f.dir ? "directory" : "regular") +
                "\nSize: " +
                (f.dir ? 0 : f.text.length) +
                "\nAccess: " +
                (f.locked ? "0000 / locked" : "0640") +
                (f.locked
                  ? "\nLock: CIS-STATIC/1\nIndex: " + (located ? "resolved" : "unresolved")
                  : ""),
            );
            return;
          }
          if (cmd === "grep") {
            if (a.length !== 2) usage(cmd);
            var rows = textFile(path(a[1])).split("\n");
            rows.forEach(function (l, i) {
              if (l.includes(a[0])) write(i + 1 + ":" + l);
            });
            return;
          }
          if (cmd === "ping") {
            if (a.length) usage(cmd);
            if (connected) fail("aux: EBUSY");
            busy = true;
            write("aux0: tx 64 bytes", "dim");
            await pause(650);
            live(token);
            write("aux0: rx D-04 / ttl=64 / time=3.7 ms");
            await pause(400);
            live(token);
            discovered = true;
            write(
              "1102/tcp  closed   diag\n2204/tcp  denied   control\n" +
                port +
                "/tcp  open     cis-archive/1",
            );
            emit("port-discovered", { port: port, target: "D-04" });
            return;
          }
          if (cmd === "connect") {
            if (a.length !== 1) usage(cmd);
            if (connected) fail("aux: EISCONN");
            if (!discovered) fail("aux: ENXIO");
            var address = a[0].replace(/^aux:\/\/D-04:/i, "");
            if (address !== port) fail("connect: ECONNREFUSED");
            busy = true;
            await pause(650);
            live(token);
            connected = true;
            dir("/cis");
            dir("/cis/sys");
            dir("/cis/var");
            dir("/cis/var/cache");
            dir("/cis/var/cache/cmd");
            add(
              "/cis/sys/node.conf",
              "node=D-04\nnetwork=CIS\narchive_root=/var/cache/cmd\nsecurity=STATIC/1",
            );
            add("/cis/var/cache/session.idx", "0008|cmd|rw|CIS-STATIC/1");
            if (!fs[target])
              add(
                target,
                "CIS / D-04\nGARRISON ORDERS\n\nShift: 03:00-07:00\nNorth gate: B1 / 12 units\nReserve: sector 07\nSupply route: R-17\n",
                true,
              );
            write("aux://D-04:" + port + " connected\nvolume mounted at /cis", "dim");
            prompt();
            emit("connected", { port: port });
            return;
          }
          if (cmd === "find") {
            // Без пути поиск начинается в текущем каталоге.
            var searchPath = cwd,
              pattern = "*";
            if (a.length === 1) {
              var candidatePath = path(a[0]);
              if (
                (fs[candidatePath] && fs[candidatePath].dir) ||
                (a[0].includes("/") && !/[?*]/.test(a[0]))
              ) {
                searchPath = a[0];
              } else if (a[0] === "-name") usage(cmd);
              else pattern = a[0];
            } else if (a.length === 2) {
              if (a[0] !== "-name") searchPath = a[0];
              pattern = a[1];
            } else if (a.length === 3 && a[1] === "-name") {
              searchPath = a[0];
              pattern = a[2];
            } else if (a.length > 0) usage(cmd);
            var root = path(searchPath);
            if (!item(root).dir) fail(root + ": ENOTDIR");
            var regex = new RegExp(
              "^" +
                pattern
                  .replace(/[.+^{}$()|[\]\\]/g, "\\$&")
                  .replace(/\*/g, ".*")
                  .replace(/\?/g, ".") +
                "$",
            );
            var matches = Object.keys(fs)
              .filter(function (p) {
                return (p === root || p.startsWith(root + "/")) && regex.test(p.split("/").pop());
              })
              .sort();
            if (isRemote(root) && matches.indexOf(target) >= 0 && !located) {
              busy = true;
              var scan = write("[find] Сканирование файлового индекса…", "dim"),
                cycle = 0;
              while (!located) {
                await pause(700);
                live(token);
                cycle++;
                scan.textContent =
                  "[find] " +
                  ["Сканирование блоков…", "Повторная индексация…", "Проверка сигнатур…"][
                    cycle % 3
                  ];
                if (roll("INDEX")) {
                  located = true;
                  scan.textContent = "[find] Индекс восстановлен. Файл обнаружен.";
                  emit("target-located", { path: target });
                }
              }
            }
            if (matches.length)
              matches.forEach(function (p) {
                write(p);
              });
            else write("Совпадений не найдено.", "dim");
            return;
          }
          if (cmd === "edit") {
            if (a.length !== 1) usage(cmd);
            openEditor(path(a[0]));
            return;
          }
          if (cmd === "run") {
            var program = a[0] && a[0].split("/").pop();
            if (
              ["bruteforce", "multiforce", "encryptor"].includes(program) &&
              a[0].indexOf("/") >= 0
            ) {
              if (path(a[0]) !== "/datapad/" + program) fail("run: программа не найдена");
            }
            if (["bruteforce", "multiforce", "encryptor"].includes(program)) {
              if (a.length !== 2) usage(cmd);
              if (!connected) fail("bruteforce: нет соединения с консолью");
              if (!located) fail("bruteforce: сначала найдите защищённый файл");
              var filePath = path(a[1]);
              item(filePath);
              if (filePath !== target) fail("bruteforce: этот файл не является целью");
              if (!fs[target].locked) fail("bruteforce: файл уже открыт");
              if (program === "encryptor") {
                write("[encryptor] CIS-STATIC/1: преобразование ключа не требуется.", "dim");
                return;
              }
              busy = true;
              var fast = roll(program === "multiforce" ? "MF-01" : "BF-01"),
                total = attemptLimit;
              write("[" + program + "] " + filePath, "dim");
              write("Подбор статического ключа…", "dim");
              var stream = write("", "dim"),
                counter = write("", "dim"),
                batchSize = Math.max(1, Math.ceil(total / (fast ? 48 : 132))),
                frames = Math.ceil((matchIndex + 1) / batchSize);
              for (var frame = 1; frame <= frames; frame++) {
                await pause((fast ? 3800 : 10500) / (fast ? 48 : 132));
                live(token);
                // Последняя пачка обрывается сразу на найденном ключе.
                var checked = Math.min(frame * batchSize, matchIndex + 1),
                  rows = [];
                for (var n = Math.max(0, checked - 6); n < checked; n++) {
                  var candidate = candidateCode(n);
                  rows.push(
                    "> " + candidate + "  " + (candidate === secret ? "[ MATCH ]" : "[ REJECT ]"),
                  );
                }
                stream.textContent = rows.join("\n");
                counter.textContent =
                  checked.toLocaleString("ru-RU") +
                  " / " +
                  total.toLocaleString("ru-RU") +
                  " combinations";
                if (frame === frames) stream.className = "line ok";
                out.scrollTop = out.scrollHeight;
              }
              keyRecovered = true;
              write("KEY RECOVERED: " + secret, "ok");
              emit("key-recovered", { file: target });
              return;
            }
            if (a.length !== 1) usage(cmd);
            busy = true;
            await runScript(path(a[0]), token);
            return;
          }
          if (cmd === "unlock") {
            if (a.length !== 3 || a[1] !== "--key") usage(cmd);
            var p = path(a[0]),
              f = item(p);
            if (p !== target || !located) fail("unlock: unresolved target");
            if (!f.locked) fail("unlock: EALREADY");
            if (a[2] !== secret) fail("unlock: EKEYREJECTED");
            f.locked = false;
            write(p + ": access mode 0640", "ok");
            emit("unlocked", { path: p });
            return;
          }
          if (cmd === "cp") {
            if (a.length !== 2) usage(cmd);
            var from = path(a[0]),
              text = textFile(from),
              to = path(a[1]);
            if (fs[to] && fs[to].dir) to += "/" + from.split("/").pop();
            writable(to);
            busy = true;
            await pause(900);
            live(token);
            add(to, text);
            write(text.length + " bytes written", "dim");
            if (from === target && to.startsWith("/datapad/") && !completed) {
              completed = true;
              write("transfer complete", "ok");
              prompt();
              emit("completed", { file: from, destination: to });
            }
            return;
          }
          fail(cmd + ": command not found");
        }

        // Новая сессия: два каталога, готовые программы, новый порт, файл и ключ.
        function reset() {
          epoch++;
          session++;
          fs = {};
          cwd = "/datapad";
          connected = false;
          discovered = false;
          located = false;
          completed = false;
          busy = false;
          moduleReady = true;
          keyRecovered = false;
          nextRoll = null;
          lastRoll = null;
          history = [];
          hi = 0;
          draft = "";
          port = String(4100 + rand(800));
          keySeed = rand(4294967295);
          attemptLimit = 2000000 + rand(8000000);
          // Правильный ключ занимает случайную позицию внутри диапазона.
          matchIndex = rand(attemptLimit);
          secret = candidateCode(matchIndex);
          target =
            "/cis/var/cache/cmd/" + ("orders_" + String(rand(256)).padStart(3, "0")) + ".dat";
          [
            "/",
            "/datapad",
            "/cis",
            "/datapad/bin",
            "/datapad/dev",
            "/datapad/etc",
            "/datapad/data",
            "/datapad/usr",
            "/datapad/usr/include",
            "/datapad/usr/share",
            "/datapad/usr/share/dicts",
          ].forEach(dir);
          ["bruteforce", "multiforce", "encryptor"].forEach(function (name) {
            add("/datapad/" + name, "VAR executable / " + name + "\n");
          });
          commands
            .slice()
            .sort()
            .forEach(function (name) {
              add("/datapad/bin/" + name, "ELF\nVAR executable / " + name);
            });
          add("/datapad/dev/aux0", "state=physical-link\nrx=0\ntx=0");
          add(
            "/datapad/etc/device.conf",
            "hostname=var-pad\ninterface=aux0\nmountpoint=/cis\ntransfer_root=/datapad/data",
          );
          add(
            "/datapad/usr/include/cis.h",
            "typedef string path;\nextern string[] readlines(path file);\nextern bool probe(path target, string candidate);\nextern void print(string value);\n\nABI: CIS-STATIC/1\nVM: var-js / let,const,for-of,if,break\n",
          );
          var keys = [],
            keySlot = rand(5000);
          for (var i = 0; i < 5000; i++) keys.push(i === keySlot ? secret : candidateCode(i));
          add("/datapad/usr/share/dicts/static.keys", keys.join("\n"));
          add("/datapad/.profile", "HOST=var-pad\nPATH=/datapad/bin\nVM=var-js");
          if (editing) closeEditor();
          input.value = "";
          out.textContent = "";
          write("VAR/OS 4.7.12  [tty0]", "dim");
          write("aux0: carrier detected", "dim");
          write("");
          prompt();
          input.focus();
          emit("reset");
        }

        // Клавиатура консоли: выполнение команды, история, очистка и прерывание.
        $("form").addEventListener("submit", async function (e) {
          e.preventDefault();
          var raw = input.value.trim();
          if (!raw) return;
          history.push(raw);
          if (history.length > 100) history.shift();
          hi = history.length;
          input.value = "";
          draft = "";
          write($("prompt").textContent + " " + raw, "command");
          if (busy) {
            if (["help", "status", "clear", "disconnect"].includes(raw.split(/\s+/)[0])) {
              execute(raw).catch(function (e) {
                write(e.message, "err");
              });
            } else write("shell: device busy", "err");
            return;
          }
          var token = epoch;
          try {
            await execute(raw);
          } catch (e) {
            if (token === epoch) write(e.message, "err");
          } finally {
            if (token === epoch) {
              busy = false;
              prompt();
            }
          }
        });

        // Автодополнение по Tab: команды, уровни справки, программы и пути.
        function complete() {
          var value = input.value,
            position = input.selectionStart;
          if (position !== input.selectionEnd) return;
          var left = value.slice(0, position),
            right = value.slice(position),
            m = left.match(/(?:^|\s)([^\s]*)$/);
          if (!m) return;
          var prefix = m[1],
            start = position - prefix.length,
            head = left.slice(0, start),
            words = head.trim().split(/\s+/).filter(Boolean),
            cmd = words[0] || "",
            arg = words.length,
            candidates = [];
          if (words.length === 0) {
            candidates = commands.filter(function (x) {
              return x.startsWith(prefix);
            });
          } else if (
            cmd === "run" &&
            arg === 1 &&
            prefix.indexOf("/") < 0 &&
            ["bruteforce", "multiforce", "encryptor"].some(function (x) {
              return x.startsWith(prefix);
            })
          ) {
            candidates = ["bruteforce", "multiforce", "encryptor"].filter(function (x) {
              return x.startsWith(prefix);
            });
          } else if (cmd === "help" && arg === 1) {
            candidates = Object.keys(levelGuides).filter(function (x) {
              return x.startsWith(prefix);
            });
          } else if (cmd === "connect" && arg === 1) {
            if (discovered && port.startsWith(prefix)) candidates = [port];
          } else if (cmd === "find" && arg <= 2 && prefix.startsWith("-")) {
            candidates = ["-name"].filter(function (x) {
              return x.startsWith(prefix);
            });
          } else if (cmd === "unlock" && arg === 2) {
            candidates = ["--key"].filter(function (x) {
              return x.startsWith(prefix);
            });
          } else if (
            (cmd === "unlock" && arg >= 3) ||
            (cmd === "find" && arg >= 3) ||
            (cmd === "grep" && arg === 1) ||
            ["help", "status", "clear", "ping", "pwd", "disconnect"].includes(cmd)
          ) {
            return;
          } else {
            var slash = prefix.lastIndexOf("/"),
              lead = slash >= 0 ? prefix.slice(0, slash + 1) : "",
              stem = slash >= 0 ? prefix.slice(slash + 1) : prefix,
              base = path(lead || cwd);
            if (isRemote(base) && !connected) return;
            if (!fs[base] || !fs[base].dir) return;
            Object.keys(fs).forEach(function (p) {
              if (parent(p) !== base || p === "/") return;
              var name = p.split("/").pop();
              if (!name.startsWith(stem) || (name[0] === "." && stem[0] !== ".")) return;
              if (cmd === "cd" && !fs[p].dir) return;
              candidates.push(lead + name + (fs[p].dir ? "/" : ""));
            });
          }
          candidates.sort();
          if (!candidates.length) return;
          var replacement = candidates[0];
          if (candidates.length > 1) {
            for (var n = 1; n < candidates.length; n++) {
              var j = 0;
              while (
                j < replacement.length &&
                j < candidates[n].length &&
                replacement[j] === candidates[n][j]
              )
                j++;
              replacement = replacement.slice(0, j);
            }
            write(candidates.join("  "), "dim");
          } else if (!replacement.endsWith("/") && (!right || !/^\s/.test(right)))
            replacement += " ";
          input.value = head + replacement + right;
          input.setSelectionRange(
            head.length + replacement.length,
            head.length + replacement.length,
          );
        }
        input.addEventListener("keydown", function (e) {
          if (e.key === "Tab") {
            e.preventDefault();
            complete();
            return;
          }
          if (e.key === "ArrowUp" || e.key === "ArrowDown") {
            e.preventDefault();
            if (hi === history.length) draft = input.value;
            if (e.key === "ArrowUp" && hi > 0) hi--;
            if (e.key === "ArrowDown" && hi < history.length) hi++;
            input.value = hi === history.length ? draft : history[hi];
            input.setSelectionRange(input.value.length, input.value.length);
          }
          if (e.ctrlKey && e.key.toLowerCase() === "l") {
            e.preventDefault();
            out.textContent = "";
          }
          if (e.ctrlKey && e.key.toLowerCase() === "c") {
            e.preventDefault();
            epoch++;
            busy = false;
            input.value = "";
            write("^C", "dim");
            prompt();
          }
        });

        // Клавиатура редактора и отметка несохранённых изменений.
        source.addEventListener("input", function () {
          dirty = source.value !== editorOriginal;
          $("editState").textContent = dirty ? "*" : "";
          numbers();
        });
        source.addEventListener("scroll", numbers);
        source.addEventListener("keydown", function (e) {
          if (e.ctrlKey && e.key.toLowerCase() === "s") {
            e.preventDefault();
            add(editing, source.value);
            editorOriginal = source.value;
            dirty = false;
            $("editState").textContent = "written " + source.value.length + " bytes";
          } else if (e.key === "Escape") {
            e.preventDefault();
            if (dirty) {
              $("editState").textContent = "unsaved buffer";
              return;
            }
            closeEditor();
          } else if (e.key === "Tab") {
            e.preventDefault();
            var start = source.selectionStart,
              end = source.selectionEnd;
            source.setRangeText("  ", start, end, "end");
            source.dispatchEvent(new Event("input"));
          }
        });

        // Публичный API для интеграции. Роль назначается модом, а не командой игрока.
        window.KNSHack = Object.freeze({
          getState: snapshot,
          reset: reset,
          setRole: function (value) {
            if (connected || busy) fail("role locked");
            if (!["standard", "engineer"].includes(value)) fail("invalid role");
            role = value;
          },
          setNextRoll: function (value) {
            if (busy || !Number.isInteger(value) || value < 0 || value > 100) fail("invalid roll");
            nextRoll = value;
          },
        });
        reset();
      })();
    </script>
  </body>
</html>
