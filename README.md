<!DOCTYPE html>
<html>
<head>
    <title>Grade Computation</title>
</head>
<body>
    <h1>Grade Computation</h1>
    <form method="post" action="">
        <?php
        $subjects = array('Math', 'Science', 'English', 'History', 'Art', 'Physical Education');
        foreach ($subjects as $subject) {
            echo "<label for='$subject'>$subject: </label>";
            echo "<input type='number' name='scores[$subject]' id='$subject' min='0' max='100' required><br>";
        }
        ?>
        <input type="submit" value="Compute Grades">
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $scores = $_POST['scores'];

        $total_score = array_sum($scores);
        $average_score = $total_score / count($scores);

        if ($average_score >= 90) {
            $grade = 'A';
        } elseif ($average_score >= 80) {
            $grade = 'B';
        } elseif ($average_score >= 70) {
            $grade = 'C';
        } elseif ($average_score >= 60) {
            $grade = 'D';
        } else {
            $grade = 'F';
        }

        echo "<h2>Results</h2>";
        echo "Total Score: $total_score<br>";
        echo "Average Score: $average_score<br>";
        echo "Grade: $grade<br>";
    }
    ?>
</body>
</html>
