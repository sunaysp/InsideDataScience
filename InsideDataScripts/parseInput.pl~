print "Starting \n";

# Opening three file pointers.
open(F,"<./tweet_input/input_tweets.txt") or die("cannot open file");
open(F1,">./tweet_output/ft1.txt") or die("Cannot open file");
open(F2,">./tweet_output/ft2.txt") or die("Cannot open file");

my %hash; #Used for wordcount for the entire file. Key is word and value is count
my @uniqueWordCount; #Stores the unique word count in each tweet and used to calculate median
my $index=0;
while($line=<F>) {
	@words = split(/\s+/,$line);
	my %uniquewords; # Used to store unique words for each tweet. Local scope
	foreach $word(@words) {
		if(exists($hash{$word})) { # If word exists in hash, increment the count
			$hash{$word}++;
		} else { # If not exists, create a new record 
			$hash{$word}=1;
		}
		if(!exists($uniquewords{$word})) { # stores only unique words. 
			$uniquewords{$word}=1;
		}
	}
	$uniqueWordCount{$index}=keys %uniquewords;
	$index++;
	# calculating median
	$length = $index;
	if($length==1) {
		print F2 "$uniqueWordCount{0}\n";
	} elsif($length>1 && ($length%2==0)) {
		$mid = $length/2;
		$median = ($uniqueWordCount{$mid}+$uniqueWordCount{$mid-1})/2;
		print F2 "$median\n";
	} elsif($length>1 && ($length%2!=0)) {
		$median = $uniqueWordCount{$mid};
		print F2 "$median\n";
	}
}

foreach my $key (sort keys %hash) {
	print F1 $key,"\t", $hash{$key}."\n";
}
