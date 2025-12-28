<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>January Devotions</title>

<style>
body{
  margin:0;
  font-family: Inter, Arial, sans-serif;
  background:#f8f6f2;
  color:#2b2b2b;
}
header{
  background:#4a3728;
  color:#fff;
  padding:20px;
  text-align:center;
}
.container{
  max-width:900px;
  margin:auto;
  padding:20px;
}
.card{
  background:#fff;
  padding:20px;
  border-radius:8px;
  box-shadow:0 4px 10px rgba(0,0,0,.05);
}
h2,h3{color:#4a3728}
.date{color:#777;font-size:14px}
.buttons{
  display:flex;
  justify-content:space-between;
  margin-top:20px;
}
button{
  background:#4a3728;
  color:#fff;
  border:none;
  padding:10px 16px;
  border-radius:5px;
  cursor:pointer;
}
button:disabled{
  background:#999;
  cursor:not-allowed;
}
.progress{
  margin-top:15px;
  font-weight:600;
  color:#4a3728;
}
footer{
  background:#4a3728;
  color:#fff;
  text-align:center;
  padding:15px;
  margin-top:30px;
}
</style>
</head>

<body>

<header>
  <h1>📖 January Devotions</h1>
  <p>Read • Reflect • Pray</p>
</header>

<div class="container">

<section class="card">
  <h2 id="title"></h2>
  <p class="date" id="date"></p>

  <h3>📜 Bible Reading</h3>
  <p id="reading"></p>

  <h3>📝 Devotional Thought</h3>
  <p id="devotion"></p>

  <h3>🙏 Prayer</h3>
  <p id="prayer"></p>

  <h3>🎯 Action Point</h3>
  <p id="action"></p>

  <div class="buttons">
    <button id="prevBtn">⬅ Previous</button>
    <button id="nextBtn">Next ➡</button>
  </div>

  <div class="progress" id="progress"></div>
</section>

</div>

<footer>
  <p>© 2025 Daily Devotion</p>
</footer>

<script>
const january = [
{day:1,title:"A New Beginning",reading:"Genesis 1:1–5 | Matthew 1:1–17 | Psalm 1",devotion:"God specializes in new beginnings. He creates light out of darkness and hope out of despair.",prayer:"Lord, thank You for a new beginning. Order my steps this year. Amen.",action:"Commit this year fully to God."},
{day:2,title:"Walking in God’s Light",reading:"Genesis 1:6–13 | Matthew 1:18–25 | Psalm 2",devotion:"God’s light brings clarity and direction. Walking in His truth leads to peace.",prayer:"Father, guide me in Your light. Amen.",action:"Choose obedience today."},
{day:3,title:"Created With Purpose",reading:"Genesis 1:14–25 | Matthew 2:1–12 | Psalm 3",devotion:"You were created intentionally by God. Your life carries meaning.",prayer:"Lord, help me live my purpose. Amen.",action:"Speak positively about your future."},
{day:4,title:"Made in God’s Image",reading:"Genesis 1:26–31 | Matthew 2:13–23 | Psalm 4",devotion:"Being made in God’s image gives your life value and dignity.",prayer:"Father, help me reflect You. Amen.",action:"Honor others."},
{day:5,title:"Rest Is God’s Idea",reading:"Genesis 2:1–3 | Matthew 3 | Psalm 5",devotion:"Rest renews strength and builds trust in God.",prayer:"Lord, teach me to rest in You. Amen.",action:"Spend quiet time with God."},
{day:6,title:"Obedience Brings Life",reading:"Genesis 2:4–17 | Matthew 4:1–11 | Psalm 6",devotion:"Obedience keeps us aligned with God’s will.",prayer:"Father, strengthen my obedience. Amen.",action:"Resist temptation."},
{day:7,title:"God Values Relationship",reading:"Genesis 2:18–25 | Matthew 4:12–25 | Psalm 7",devotion:"God created us for meaningful relationships.",prayer:"Lord, help me build godly relationships. Amen.",action:"Encourage someone."},
{day:8,title:"Guard Your Heart",reading:"Genesis 3:1–7 | Matthew 5:1–12 | Psalm 8",devotion:"Your heart determines the direction of your life.",prayer:"Father, guard my heart. Amen.",action:"Filter influences."},
{day:9,title:"God Seeks Restoration",reading:"Genesis 3:8–15 | Matthew 5:13–26 | Psalm 9",devotion:"God desires restoration, not destruction.",prayer:"Lord, restore me. Amen.",action:"Return to God."},
{day:10,title:"Grace Still Covers",reading:"Genesis 3:16–24 | Matthew 5:27–48 | Psalm 10",devotion:"God’s grace remains even after failure.",prayer:"Father, help me walk in grace. Amen.",action:"Accept correction."},
{day:11,title:"True Worship",reading:"Genesis 4:1–7 | Matthew 6:1–18 | Psalm 11",devotion:"God desires sincere worship.",prayer:"Lord, accept my worship. Amen.",action:"Give God your best."},
{day:12,title:"Choose Peace",reading:"Genesis 4:8–16 | Matthew 6:19–34 | Psalm 12",devotion:"Peace preserves life and relationships.",prayer:"Father, help me choose peace. Amen.",action:"Let go of anger."},
{day:13,title:"Faithfulness Matters",reading:"Genesis 4:17–26 | Matthew 7 | Psalm 13",devotion:"God honors consistency.",prayer:"Lord, help me stay faithful. Amen.",action:"Be consistent in prayer."},
{day:14,title:"Walking With God",reading:"Genesis 5 | Matthew 8 | Psalm 14",devotion:"Walking with God builds intimacy.",prayer:"Father, walk with me today. Amen.",action:"Talk to God often."},
{day:15,title:"Obedience Saves",reading:"Genesis 6:1–8 | Matthew 9 | Psalm 15",devotion:"Obedience positions us for protection.",prayer:"Lord, help me obey. Amen.",action:"Follow God promptly."},
{day:16,title:"Faith Requires Action",reading:"Genesis 6:9–22 | Matthew 10 | Psalm 16",devotion:"Faith must be acted upon.",prayer:"Father, strengthen my faith. Amen.",action:"Take a faith step."},
{day:17,title:"God Keeps Promises",reading:"Genesis 7 | Matthew 11 | Psalm 17",devotion:"God’s promises never fail.",prayer:"Lord, I trust Your Word. Amen.",action:"Hold onto God’s promise."},
{day:18,title:"God Remembers You",reading:"Genesis 8 | Matthew 12 | Psalm 18",devotion:"God never forgets His people.",prayer:"Father, thank You for remembering me. Amen.",action:"Wait patiently."},
{day:19,title:"Covenant Keeping God",reading:"Genesis 9:1–17 | Matthew 13 | Psalm 19",devotion:"God remains faithful to His covenant.",prayer:"Lord, thank You for Your faithfulness. Amen.",action:"Trust God fully."},
{day:20,title:"God Is the Source",reading:"Genesis 9:18–29 | Matthew 14 | Psalm 20",devotion:"Every blessing comes from God.",prayer:"Father, bless the work of my hands. Amen.",action:"Acknowledge God as source."},
{day:21,title:"Set Apart",reading:"Genesis 10 | Matthew 15 | Psalm 21",devotion:"God calls His people to live differently.",prayer:"Lord, set me apart. Amen.",action:"Live for God."},
{day:22,title:"A Humble Heart",reading:"Genesis 11:1–9 | Matthew 16 | Psalm 22",devotion:"God resists pride but honors humility.",prayer:"Father, keep me humble. Amen.",action:"Give God glory."},
{day:23,title:"Faith Requires Movement",reading:"Genesis 12:1–9 | Matthew 17 | Psalm 23",devotion:"Faith often requires leaving comfort.",prayer:"Lord, help me trust You. Amen.",action:"Step out in faith."},
{day:24,title:"God Our Shield",reading:"Genesis 13 | Matthew 18 | Psalm 24",devotion:"God protects those who trust Him.",prayer:"Father, be my shield. Amen.",action:"Choose peace."},
{day:25,title:"Victory Through Faith",reading:"Genesis 14 | Matthew 19 | Psalm 25",devotion:"Faith positions us for victory.",prayer:"Lord, grant me victory. Amen.",action:"Trust God in battles."},
{day:26,title:"God Is Enough",reading:"Genesis 15 | Matthew 20 | Psalm 26",devotion:"God Himself is our reward.",prayer:"Father, You are enough. Amen.",action:"Value God above all."},
{day:27,title:"Waiting on God",reading:"Genesis 16 | Matthew 21 | Psalm 27",devotion:"Waiting builds patience and faith.",prayer:"Lord, help me wait well. Amen.",action:"Avoid rushing God."},
{day:28,title:"Covenant Faithfulness",reading:"Genesis 17 | Matthew 22 | Psalm 28",devotion:"God calls us to faithful obedience.",prayer:"Father, keep me faithful. Amen.",action:"Renew commitment."},
{day:29,title:"Power of Intercession",reading:"Genesis 18 | Matthew 23 | Psalm 29",devotion:"God hears prayers for others.",prayer:"Lord, use me as an intercessor. Amen.",action:"Pray for someone."},
{day:30,title:"God Delivers",reading:"Genesis 19 | Matthew 24 | Psalm 30",devotion:"God rescues the righteous.",prayer:"Father, thank You for deliverance. Amen.",action:"Trust God in trials."},
{day:31,title:"God Restores",reading:"Genesis 20 | Matthew 25 | Psalm 31",devotion:"God restores peace, dignity, and purpose.",prayer:"Lord, restore my life. Amen.",action:"End the month with gratitude."}
];

let currentDay = parseInt(localStorage.getItem("janDay")) || 0;
let readDays = JSON.parse(localStorage.getItem("janRead")) || [];

function loadDay(i){
  const d = january[i];
  document.getElementById("title").innerText = `January ${d.day} — ${d.title}`;
  document.getElementById("date").innerText = `January ${d.day}`;
  document.getElementById("reading").innerText = d.reading;
  document.getElementById("devotion").innerText = d.devotion;
  document.getElementById("prayer").innerText = d.prayer;
  document.getElementById("action").innerText = d.action;
  document.getElementById("prevBtn").disabled = i === 0;
  document.getElementById("nextBtn").disabled = i === january.length - 1;
  document.getElementById("progress").innerText =
    `Progress: ${readDays.length} / 31 days completed`;
}

document.getElementById("nextBtn").onclick = () => {
  if(confirm("Have you read and reflected on today’s devotion?")){
    if(!readDays.includes(currentDay)){
      readDays.push(currentDay);
      localStorage.setItem("janRead", JSON.stringify(readDays));
    }
    if(currentDay < january.length - 1){
      currentDay++;
      localStorage.setItem("janDay", currentDay);
      loadDay(currentDay);
    }
  }
};

document.getElementById("prevBtn").onclick = () => {
  if(currentDay > 0){
    currentDay--;
    localStorage.setItem("janDay", currentDay);
    loadDay(currentDay);
  }
};

loadDay(currentDay);
</script>

</body>
</html>
